# Contributing to mcp-trust-plane

First off, thank you for taking the time to contribute! 🎉

`mcp-trust-plane` is an open-source project dedicated to bringing fine-grained, real-time data protection to agentic workflows. We openly welcome community contributions, bug fixes, features, and documentation improvements.

To maintain the architectural integrity and security standards required for enterprise data planes, all incoming Pull Requests (PRs) must undergo a structured review process by our core maintainers before being merged.

---

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct [https://github.com/abluva-research/mcp-trust-plane/blob/main/.github/CODE_OF_CONDUCT.md] Please treat all maintainers and contributors with respect.

## How Can I Contribute?

### 1. Reporting Bugs
* Check the [Issues Tab] to ensure the bug hasn't already been reported.
* If it is a new issue, open a bug report using our issue template.
* Provide a clear description, reproduction steps, and context about your MCP host/gateway environment.

### 2. Proposing Features
* We highly encourage sharing ideas! Open an issue with the tag `enhancement`.
* For major architectural changes (e.g., adding a new proxy layer or an entire policy engine module), please discuss it with the maintainers in the issue tracker *before* writing code.

### 3. Submitting Pull Requests (PRs)

We follow a strict **Fork-and-Pull** model. Anyone can contribute code by following these steps:

1. **Fork the Repository:** Create your own copy of `mcp-trust-plane`.
2. **Create a Feature Branch:** Branch off from `main` (e.g., `git checkout -b feature/jira-schema-validation`).
3. **Commit Your Changes:** Write clean code, adhere to our linting/styling guidelines, and ensure you include tests for new functionality.
4. **Push and Open a PR:** Push your branch to your fork and open a Pull Request against our `main` branch.

---

## Our PR Review Process (What to Expect)

Because this is a security and data protection layer, we enforce a strict branch protection policy:

* **Automated Checks:** Once a PR is opened, our CI/CD pipelines will automatically run tests and linters. These must pass before a human review can begin.
* **Code Owner Review:** Your PR will be automatically assigned to our core maintainers via GitHub's `CODEOWNERS` configuration. 
* **The Approval Requirement:** Community members are welcome to comment and review, but **two core maintainers approval is required** for the PR to merge. 
* **Post-Approval Changes:** If you push new commits after receiving an approval, the approval will reset automatically. This ensures the finalized code is always verified.

---

## Development Setup

To get started with local development on the proxy engine:

```bash
# Clone your fork
git clone https://github.com/mcp-trust-plane

# Install dependencies (Update this based on your stack, e.g., npm, pip, cargo)
npm install 

# Run tests
npm test
```

Thank you again for helping make agentic workflows safer for everyone!
