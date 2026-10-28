# Contributing

Thanks for contributing to Hexagon Mining Infrastructure. This is the default guide for every
repository in the organisation; a repository's own `CONTRIBUTING.md` takes precedence.

## Before you start

1. **Find the right repository** — see the [Repository Guide](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/repository-guide.md).
2. **Check for an existing issue / Jira ticket** (`CPDS-XXX`). Create one for anything non-trivial.
3. **Read the [best practices](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/README.md)**,
   and the repository's `README.md` / `AGENTS.md`.

## Workflow

```bash
git clone https://github.com/Hexagon-Mining-Infrastructure/<repo>.git
cd <repo>
pre-commit install
git switch -c feature/CPDS-123-short-description

# …make changes…
pre-commit run --all-files
git commit -S -s -m "feat(scope): add something useful"
git push -u origin HEAD
gh pr create --fill --draft
```

Checklist before requesting review:

- [ ] Branch name follows [conventions](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/git-workflow.md#branches)
- [ ] Commits are Conventional, GPG-signed and DCO signed-off
- [ ] `pre-commit run --all-files` passes
- [ ] Docs updated (`.header.md` / README / repository guide)
- [ ] For live repos: `terraform plan` attached and reviewed
- [ ] PR template completed and Jira issue linked

## Questions

Ask in [Discussions](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions). See [SUPPORT.md](SUPPORT.md).
