# Contributing to mcp-trust-plane

Thanks for your interest in contributing! This guide walks through how to propose changes to this repo.

## Repository Structure

Before contributing, it helps to understand the layout:

- **`common/`** — shared, standalone MCP filters (e.g. `field-masker`, `pii-redactor`, `rate-limiter`, `row-limiter`, `schema-validator`, `sql-guard`). Each has its own `Dockerfile`, `index.js`, and `package.json`.
- **`provider/`** — provider-specific `data-guard` integrations (e.g. `github/data-guard`, `slack/data-guard`). These depend on shared code in `provider/_lib/`.
- **`docs/`** — architecture and contract documentation. If you're adding a new filter or provider, check `docs/ADDING_FILTERS.md` and `docs/CONTRACT.md` first.

## How to Contribute

### 1. Fork the repository

Click **Fork** at the top of the repo page to create your own copy under your GitHub account.

### 2. Clone your fork

```
git clone https://github.com/<your-username>/mcp-trust-plane.git
cd mcp-trust-plane
```

### 3. Create a feature branch

Branch off `main` using one of the following prefixes depending on the change type:

- `feature/<short-description>` — new functionality (e.g. `feature/add-redis-data-guard`)
- `fix/<short-description>` — bug fixes (e.g. `fix/sql-guard-escape-bug`)
- `docs/<short-description>` — documentation-only changes
- `chore/<short-description>` — tooling, CI, dependency bumps

Example:
```
git checkout -b feature/add-redis-data-guard
```

### 4. Make your changes

- Keep each filter/provider self-contained — avoid cross-importing between unrelated services.
- If adding a new filter under `common/` or a new provider integration under `provider/`, follow the existing folder pattern (`Dockerfile`, `index.js`, `package.json`) and update `provider/manifest.json` if applicable.
- Update relevant docs (`docs/ADDING_FILTERS.md`, `docs/ARCHITECTURE.md`, `docs/CONTRACT.md`) if your change affects the filter contract or architecture.

### 5. Commit your changes

Write clear, descriptive commit messages explaining *why*, not just *what*.

### 6. Push to your fork

```
git push origin <your-branch-name>
```

### 7. Open a Pull Request

Open a PR against `main` on the upstream repo. In the PR description, include:
- What the change does and why
- Which filter(s) or provider(s) are affected
- Any testing performed

## Review Process

All PRs are openly welcomed but require approval from our core maintainers before merging, to ensure architectural alignment with the rest of the filter and provider ecosystem.
