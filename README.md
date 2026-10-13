# app-recall-tracker

> [!WARNING]
> **Demonstration use only — not a CloudBees product.**
>
> This repository is part of a hands-on workshop for CloudBees Unify. It is a
> reference application built to teach concepts such as feature flags and
> progressive delivery, and it is **not** an official, supported, or maintained
> CloudBees product.
>
> **It is not safe for production use.** Authentication, access control, input
> handling and network safeguards have been deliberately simplified for teaching
> and have known security gaps. Run it only for the duration of a workshop or
> demonstration and tear it down afterwards. Do not use it with live data from
> personal, customer, or business accounts, or with any confidential
> information, and do not use it as a template for production code without a
> full security review.
>
> The recall information it displays comes from public FDA and CPSC sources and
> is shown for demonstration only; it is not compliance or legal advice.
>
> Provided "as is", without warranty of any kind, under the terms of the
> [LICENSE](LICENSE).

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
