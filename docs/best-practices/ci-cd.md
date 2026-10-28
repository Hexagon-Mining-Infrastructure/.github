# CI/CD

## Reuse before you write

| Need | Use |
|---|---|
| Lint/format/validate/docs | `terraform-composite-actions/pre-commit` |
| Security scan | `terraform-composite-actions/trivy-scan` |
| Code quality | `terraform-composite-actions/sonar-scan` |
| Module tests | `terraform-composite-actions/terratest` |
| Versioning & release | `terraform-composite-actions/semantic-version`, `auto-tag`, `publish` |
| Deploy a live workspace | `terraform-composite-actions/deploy` |
| Tear down a workspace | `terraform-composite-actions/workspace-cleanup` |
| Job context (env, deployment URL) | `actions--context` |
| AI PR review | reusable workflow in this repo (`.github/workflows/claude-pr-review.yml`) |

If the step you need doesn't exist, add it to `terraform-composite-actions` rather than inlining
scripts in many repos.

## Standard workflows per repository

| Workflow | Trigger | Purpose |
|---|---|---|
| `pr-title` | PR opened/edited | Enforce Conventional Commit PR titles |
| `pre-commit` | PR | Same hooks as local |
| `terraform-ci` | PR | `init`/`validate`/tests; `plan` for live repos |
| `nightly-security-scan` | schedule | Trivy against default branch |
| `release` | push to `main` | semantic-release + changelog |
| `stale` / `lock` | schedule | Housekeeping |

## Workflow hygiene

- **Pin third-party actions to a full commit SHA** (with a `# vX.Y.Z` comment); first-party
  org actions to a release tag. Let Dependabot/Renovate update them.
- Set `permissions:` explicitly at workflow or job level, starting from `contents: read`.
- Use **OIDC** (`aws-actions/configure-aws-credentials` with `role-to-assume`) — no long-lived AWS keys in secrets.
- Never echo secrets; avoid `pull_request_target` unless you fully understand the risk.
- Use `concurrency:` on deploy jobs so two applies never race on the same workspace.
- Protect production deploys with GitHub **Environments** and required reviewers.
- Keep jobs fast: cache plugin dirs, run expensive tests only on relevant paths.

## Required checks

Branch protection on `main` requires at least: PR title, pre-commit, terraform-ci (and plan
for live repos), and one code-owner review. Settings are managed in
`github-org-platform-governance` — change them there, not in the UI.
