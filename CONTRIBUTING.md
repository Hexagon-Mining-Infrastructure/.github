# Contributing

Thanks for contributing to Hexagon Mining Infrastructure. This is the default guide for every
repository in the organisation; a repository's own `CONTRIBUTING.md` takes precedence.

## Before you start

1. **Check for an existing issue.** Create one for anything non-trivial.
2. **Read the [best practices](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/README.md)**,
   and the repository's `README.md`.

## Workflow

```bash
git clone https://github.com/Hexagon-Mining-Infrastructure/<repo>.git
cd <repo>
git switch -c feature/<issue-id>-short-description

# …make changes, run the repository's local checks…
git commit -S -s -m "feat(scope): add something useful"
git push -u origin HEAD
gh pr create --fill --draft
```

Checklist before requesting review:

- [ ] Branch name follows [conventions](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/git-workflow.md#branches)
- [ ] Commits are Conventional, GPG-signed and DCO signed-off
- [ ] The repository's local checks pass
- [ ] Docs updated
- [ ] PR template completed and issue linked

## Questions

Ask in [Discussions](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions). See [SUPPORT.md](SUPPORT.md).
