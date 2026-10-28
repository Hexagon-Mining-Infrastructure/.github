# AI-Assisted Development

AI tools (Claude Code, Copilot, custom agents) are welcome. You remain the author and are
accountable for everything you commit.

## Agents available to the org

Custom agents live in `.github-private` (members only). Useful ones include:

| Agent | Use it for |
|---|---|
| `infrastructure-standards` | Checking work against these standards |
| `tf-module-author` | Scaffolding / validating Terraform modules |
| `workspace-validator` | Creating or debugging `terraform-live-*` workspaces |
| `terraform-preflight` | Running fmt/validate/tflint/trivy/secret checks before commit |
| `iam-policy-reviewer` | Least-privilege review of IAM changes |
| `conventional-commit` | Drafting signed Conventional Commit messages |
| `pr-describer` / `pr-reviewer` | Writing PR descriptions; working through review comments |
| `docs-sync` | Regenerating terraform-docs and catching README drift |

Each repo's `AGENTS.md` / `CLAUDE.md` gives agents repo-specific context — keep it current.

## Rules

- **Review every line** an AI produced as if a new colleague wrote it. Run the checks.
- **Never paste secrets**, credentials, customer data or state files into an AI tool.
- Use only org-approved tools and accounts.
- AI-generated commits still need GPG signing and your DCO sign-off; a `Co-Authored-By` trailer is fine.
- AI must not run `terraform apply`, push to protected branches or change IAM/org settings
  without explicit human confirmation.
- The automated Claude PR review is advisory. It does not replace human approval.

## Using the Claude PR review in your repo

```yaml
# .github/workflows/claude-review.yml
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  review:
    uses: Hexagon-Mining-Infrastructure/.github/.github/workflows/claude-pr-review.yml@main
    with:
      pr_number: ${{ github.event.pull_request.number }}
      repo: ${{ github.repository }}
    secrets:
      ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

> Pin `@main` to a tag or SHA once the workflow is released.
