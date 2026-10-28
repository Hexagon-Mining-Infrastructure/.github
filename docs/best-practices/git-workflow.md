# Git Workflow

## Branches

| Work type | Pattern | Example |
|---|---|---|
| Feature (Jira) | `feature/CPDS-XXX-short-description` | `feature/CPDS-123-add-imdsv2-enforcement` |
| Bug fix (Jira) | `bugfix/CPDS-XXX-short-description` | `bugfix/CPDS-456-fix-vpc-cidr-conflict` |
| Hotfix | `hotfix/CPDS-XXX-short-description` | `hotfix/CPDS-789-fix-prod-iam-policy` |
| Chore (no Jira) | `chore/short-description` | `chore/update-tflint-version` |

- Lowercase, hyphen-separated, short.
- **Protected branches — never push directly:** `main`, `master`, `dev`, `qa`, `staging`, `uat`, `production`.
- Delete branches after merge.

## Commits

We use [Conventional Commits](https://www.conventionalcommits.org/). Release tooling
(`semantic-release` / `semantic-version`) derives version numbers from them, so they matter.

```text
type(scope): imperative subject, lowercase, no period

- what changed and why
- what changed and why

Refs: CPDS-123
Signed-off-by: Full Name <first.last@hexagon.com>
```

**Subject:** ≤ 72 chars, imperative (`add`, not `added`), scope **required**.

| Type | Use for | Release effect |
|---|---|---|
| `feat` | New resource, variable, capability | minor |
| `fix` | Bug or misconfiguration fix | patch |
| `docs` | Documentation only | none |
| `style` | Formatting only (`terraform fmt`) | none |
| `refactor` | Restructure without behaviour change | none |
| `test` | Tests only | none |
| `chore` | Maintenance, dependency bumps, tool config | none |
| `ci` | Workflows, composite actions, Bamboo specs | none |

Breaking change → add `!` after the scope (`feat(vpc)!: …`) **and** a `BREAKING CHANGE:` footer
describing the migration. Breaking changes in modules need an `UPGRADE-x.0.md` note.

Common scopes: module/sub-module name (`mgmt-eks`, `datalake-s3`), `workspace`,
`deploy`, `trivy-scan`, `docs`, `ci`, `deps`, `config`.

## Signing: GPG + DCO

Every commit must be **GPG-signed** and carry a **DCO `Signed-off-by`** trailer.

```bash
git config --global commit.gpgsign true      # sign every commit
git commit -s -m "fix(iam): scope s3 policy to state bucket"   # -s adds Signed-off-by
```

Set up a key once:

```bash
gpg --full-generate-key
gpg --list-secret-keys --keyid-format LONG   # copy the key ID
git config --global user.signingkey <KEY_ID>
gpg --armor --export <KEY_ID>                # add to GitHub → Settings → SSH and GPG keys
```

Use your `@hexagon.com` address for both the commit author and the GPG key.

## Pull requests

- **One logical change per PR.** Multi-layer changes are separate PRs merged bottom-up.
- **PR title is a Conventional Commit** — it becomes the squash-merge commit and is checked by CI.
- Link the Jira issue (`CPDS-123`) in the title or description.
- Fill in the PR template: what, why, how tested, plan output / risk for live repos.
- Keep PRs small (aim for < 400 changed lines excluding generated docs).
- Open as **draft** until CI is green and you're ready for review.
- Rebase on the target branch rather than merging it in; keep history linear.

## Reviews

- At least **one approving review** from a code owner; **two** for `terraform-live-*` changes to
  staging/production and for anything touching IAM or networking.
- Reviewers check: correctness, security, naming/tagging, version pins, docs updated, plan output.
- Use GitHub *suggestions* for small fixes; mark nits as `nit:`.
- Authors resolve conversations only after addressing them; reviewers re-review promptly.
- An automated Claude review may comment on PRs — treat it as a reviewer's input, not an approval.

## Merging

- **Squash merge** by default; the PR title becomes the commit message.
- All required checks must pass. Don't bypass branch protection; ask a maintainer if blocked.
- After merging a module change, confirm the release/tag was published before bumping consumers.
