# Security Policy

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**  
Security flaws in MCP filters or providers handling data-guard logic can have 
serious downstream impact on applications and integrations that depend on them.

### GitHub Private Vulnerability Reporting (Preferred)

Use GitHub's built-in private reporting:
1. Go to the **Security** tab of this repository
2. Click **"Report a vulnerability"**
3. Fill in the details and submit

This is the preferred method as it keeps the disclosure private and allows 
collaborative resolution directly on GitHub.

### Email

If you are unable to use GitHub's private reporting, email us.

Please use the subject line: `[SECURITY] <brief description>`

---

## What To Include in the Report

To help us triage and resolve the issue quickly, please provide:

- **Description** — A clear summary of the vulnerability
- **Affected component** — e.g., field-masker, pii-redactor, rate-limiter, sql-guard, or a specific provider's data-guard
- **Service/package version(s)** — Which version(s) are affected
- **Node.js version** — The Node version used when the issue was observed
- **Steps to reproduce** — Minimal request payload or steps to trigger the issue
- **Potential impact** — What an attacker could achieve (e.g., filter bypass, data leakage, injection)
- **Suggested fix** — (Optional) Any ideas on how to address it

---

## Response Timeline

| Milestone                        | Target Time     |
| -------------------------------- | --------------- |
| Acknowledgement of report        | Within 48 hours |
| Initial assessment & triage      | Within 5 days   |
| Fix or mitigation                | Within 90 days  |
| Notification to reporter         | Upon release    |


---

## Disclosure Policy

We follow **coordinated responsible disclosure**:

- Please **do not publicly disclose** the vulnerability until we have released a fix
- We will credit reporters in the release notes (unless you prefer to remain anonymous)
- If a vulnerability is not resolved within 90 days, we will work with you on a 
  mutually agreed disclosure timeline

  [![OpenSSF Best Practices](https://www.bestpractices.dev/projects/13305/badge)](https://www.bestpractices.dev/projects/13305)
