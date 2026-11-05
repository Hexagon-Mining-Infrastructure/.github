# Git Workflow

## Branches

| Work type | Pattern | Example |
|---|---|---|
| Feature | `feature/<issue-id>-short-description` | `feature/123-add-encryption-enforcement` |
| Bug fix | `bugfix/<issue-id>-short-description` | `bugfix/456-fix-network-range-conflict` |
| Hotfix | `hotfix/<issue-id>-short-description` | `hotfix/789-fix-prod-access-policy` |
| Chore (no issue) | `chore/short-description` | `chore/update-linter-version` |

- Lowercase, hyphen-separated, short.
- **Protected branches — never push directly:** `main`, `master`, `dev`, `qa`, `staging`, `uat`, `production`.
- Delete branches after merge.

## Commits

We use [Conventional Commits](https://www.conventionalcommits.org/). Release tooling derives
version numbers from them, so they matter.

```text
type(scope): imperative subject, lowercase, no period

- what changed and why
- what changed and why

Refs: #123
Signed-off-by: Full Name <first.last@hexagon.com>
```

**Subject:** ≤ 72 chars, imperative (`add`, not `added`), scope **required**.

| Type | Use for | Release effect |
|---|---|---|
| `feat` | New resource, variable, capability | minor |
| `fix` | Bug or misconfiguration fix | patch |
| `docs` | Documentation only | none |
| `style` | Formatting only | none |
| `refactor` | Restructure without behaviour change | none |
| `test` | Tests only | none |
| `chore` | Maintenance, dependency bumps, tool config | none |
| `ci` | CI workflows and pipeline definitions | none |

Breaking change → add `!` after the scope (`feat(network)!: …`) **and** a `BREAKING CHANGE:` footer
describing the migration. Breaking changes need an upgrade note.

Common scopes: component name, `deploy`, `docs`, `ci`, `deps`, `config`.

## Signing: GPG + DCO

Every commit must be **GPG-signed** and carry a **DCO `Signed-off-by`** trailer.

```bash
git config --global commit.gpgsign true      # sign every commit
git commit -s -m "fix(access): scope policy to a single resource"   # -s adds Signed-off-by
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
- Link the related issue in the title or description.
- Fill in the PR template: what, why, how tested, change preview / risk for deployments.
- Keep PRs small (aim for < 400 changed lines excluding generated docs).
- Open as **draft** until CI is green and you're ready for review.
- Rebase on the target branch rather than merging it in; keep history linear.

## Reviews

- At least **one approving review** from a code owner; **two** for deployment changes to
  staging/production and for anything touching access control or networking.
- Reviewers check: correctness, security, naming, version pins, docs updated, change preview.
- Use GitHub *suggestions* for small fixes; mark nits as `nit:`.
- Authors resolve conversations only after addressing them; reviewers re-review promptly.
- Automated review comments are input, not an approval.

## Merging

- **Squash merge** by default; the PR title becomes the commit message.
- All required checks must pass. Don't bypass branch protection; ask a maintainer if blocked.
- After merging a change to a shared component, confirm the release/tag was published before bumping consumers.
