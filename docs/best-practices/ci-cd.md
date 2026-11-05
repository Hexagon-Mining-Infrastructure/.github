# CI/CD

## Reuse before you write

Shared CI steps (linting, validation, security scanning, testing, versioning, release and
deployment) live in shared, versioned actions. If the step you need doesn't exist, add it there
rather than inlining scripts in many repos.

## Standard workflows per repository

| Workflow | Trigger | Purpose |
|---|---|---|
| `pr-title` | PR opened/edited | Enforce Conventional Commit PR titles |
| Local checks | PR | Same hooks as run locally |
| Build / validate | PR | Validation and tests; change preview for deployments |
| Nightly security scan | schedule | Scan the default branch |
| `release` | push to `main` | Versioning + changelog |
| `stale` / `lock` | schedule | Housekeeping |

## Workflow hygiene

- **Pin third-party actions to a full commit SHA** (with a `# vX.Y.Z` comment); first-party
  org actions to a release tag. Let automated dependency updates bump them.
- Set `permissions:` explicitly at workflow or job level, starting from `contents: read`.
- Use **short-lived, federated credentials (OIDC)** — no long-lived keys in secrets.
- Never echo secrets; avoid `pull_request_target` unless you fully understand the risk.
- Use `concurrency:` on deploy jobs so two deployments never race on the same target.
- Protect production deploys with GitHub **Environments** and required reviewers.
- Keep jobs fast: cache dependencies, run expensive tests only on relevant paths.

## Required checks

Branch protection on `main` requires at least: PR title, local checks, build/validate (and a
change preview for deployments), and one code-owner review. Settings are managed as code —
change them there, not in the UI.
