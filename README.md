# MCP Trust Plane

A pluggable, language-agnostic filter framework for Model Context Protocol
(MCP) traffic. Each filter is a tiny HTTP service that decides whether a
tool call should be allowed, blocked, modified, or truncated.

## Why

MCP gives agents direct access to tools and data sources. That's powerful
and dangerous in equal measure. Filters give you a place to enforce
guardrails — block destructive SQL, redact PII before it reaches the
model, throttle abusive agents, cap response sizes, redact columns —
without modifying the upstream MCP server or the agent runtime.

## How it works

```
                    pre-request                       post-response
   Client ─▶ MCP Gateway ─────────▶ Engine ─▶ filter ─┐
                │     ◀────────────────── allow/block ┘
                │
                ▼ (forward)
            MCP Server
                │
                ▼
   Client ◀ MCP Gateway ◀──── Engine ─▶ filter ─┐
                                ◀───── allow/truncate/modify ┘
```

- An MCP gateway sits in front of the upstream MCP server.
- For every `tools/call`, the gateway asks an **engine** "what should I do
  for target X at execution_point Y?".
- The engine looks up the policies assigned to that target and, for each
  filter in those policies, calls `POST {filter_url}/filter`.
- Filters are completely independent processes. They can be written in
  any language. They share no state with the gateway or the engine.

A reference engine and gateway live in the parent repo
(`secure-ai-plane-x/mcp-filter-gateway`). This sub-project ships only the
filter implementations and the contract.

## The Filter Contract

Every filter MUST expose two HTTP endpoints:

### `POST /filter`

Request body:

```json
{
  "config":    { "max_rows": 1000 },
  "arguments": {
    "sql": "SELECT * FROM employees",
    "response_count": 8000,
    "response_rows": ["row-1", "row-2", "..."]
  },
  "metadata": {
    "agent_id":   "demo_agent",
    "agent_name": "demo_agent",
    "member_id":  "f5d9e4ec-…",
    "project_id": "b0000000-…",
    "tool_name":  "run_sql"
  }
}
```

Response body:

```json
{
  "action": "allow | block | truncate | modify",
  "reason": "human-readable string surfaced to the user and audit log",
  "modified_response": { "...optional..." },
  "original_count":    8000,
  "truncated_to":      1000
}
```

- `allow` — let the request through unchanged.
- `block` — reject. The gateway returns an MCP error using `reason`.
- `truncate` — return a smaller payload (`modified_response`) and an
  audit notice. Used by post-response filters like Row Limiter.
- `modify` — replace the payload with `modified_response`. Used by
  redactors and maskers.

Filters MUST be idempotent and side-effect free with respect to the
agent's behaviour (with the obvious exception of audit / rate limiter
state). Filter execution time should stay under 50ms p95; the engine
treats slow filters as `allow` to fail-open.

### `GET /health`

Returns `200 { "status": "healthy", "filter": "<slug>", "version": "..." }`.
Used by orchestrators to gate traffic.

## Common filters

Cross-cutting guards under `common/` (Apache 2.0):

| Filter           | Slug              | Phase          | Default port |
|------------------|-------------------|----------------|--------------|
| SQL Guard        | sql-guard         | pre-request    | 6001         |
| PII Redactor     | pii-redactor      | post-response  | 6002         |
| Row Limiter      | row-limiter       | post-response  | 6003         |
| Schema Validator | schema-validator  | pre-request    | 6005         |
| Rate Limiter     | rate-limiter      | pre-request    | 6007         |
| Field Masker     | field-masker      | post-response  | 6008         |

## Provider filters

Integration-specific guards under `provider/<vendor>/data-guard/` — **54
providers** today (AWS, GitHub, Stripe, Snowflake, Slack, PostgreSQL,
Notion, Terraform, and more). See `provider/README.md` and
`provider/manifest.json` for the full list and ports (6301–6354).

| Provider (sample) | Slug                   | Default port |
|-------------------|------------------------|--------------|
| AWS               | `aws-data-guard`       | 6301         |
| GitHub            | `github-data-guard`    | 6305         |
| PostgreSQL        | `postgresql-data-guard`| 6341         |
| Stripe            | `stripe-data-guard`    | 6348         |
| Slack             | `slack-data-guard`     | 6345         |

Run `node provider/scripts/generate-providers.js` after editing
`provider/manifest.json` to scaffold new vendors.

## Quickstart

```sh
cd common/sql-guard
npm install
PORT=6001 node index.js
```

Or bring up all filters with Docker:

```sh
docker compose up
```

Then register the filter against an engine:

```sql
INSERT INTO ablv_mcp_filters (slug, name, filter_url, execution_point, ...)
VALUES ('sql-guard', 'SQL Guard', 'http://sql-guard:6001/filter',
        'pre-request', ...);
```

See `docs/ADDING_FILTERS.md` for a step-by-step walkthrough of writing
your own filter.

## Layout

```
mcp-filters/
├── README.md              # this file
├── LICENSE                # Apache 2.0
├── docker-compose.yml     # common + provider filters
├── docs/
│   ├── CONTRACT.md        # full HTTP contract + JSON schema
│   ├── ARCHITECTURE.md    # how filters compose with gateway + engine
│   └── ADDING_FILTERS.md  # write-your-own walkthrough
├── common/                # cross-cutting filters (any MCP server)
│   ├── sql-guard/
│   ├── pii-redactor/
│   ├── row-limiter/
│   ├── schema-validator/
│   ├── rate-limiter/
│   └── field-masker/
├── provider/              # vendor-specific data guards (54 providers)
│   ├── manifest.json
│   ├── scripts/generate-providers.js
│   ├── _lib/
│   └── <vendor>/data-guard/
└── tests/
    ├── contract.js        # HTTP contract for every filter
    └── behaviour.js       # decision-logic regression tests
```
[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/13305/badge)](https://www.bestpractices.dev/projects/13305)
