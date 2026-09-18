# app-recall-tracker

The CloudBees Unify **Application** for the Product Recall Tracker. No source
code — this repo holds the workflows that orchestrate a release across all five
components.

| Workflow | Purpose |
|---|---|
| `verify-setup.yaml` | Checks every variable and secret is present and usable. Run this first. |
| `deployer.yaml` | Calls each component's `deploy.yaml` in dependency order. |
| `release-wf.yaml` | Staged release: DEV, approval gate, STAGING, PROD. |

## Before you start

`deployer.yaml` has five `uses:` lines containing `<YOUR_GITHUB_ORG>`.
Replace them with your GitHub username or organisation. This is the only file
that needs editing — `uses:` cannot take an expression, because Unify resolves
nested workflows before expressions are evaluated.

Everything else comes from Unify variables and secrets set in the UI.
