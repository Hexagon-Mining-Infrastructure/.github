# Engineering Best Practices

The organisation-wide engineering standards for Hexagon Mining Infrastructure. Individual
repositories may add stricter rules in their own `CONTRIBUTING.md` / `AGENTS.md`, but should
not relax these.

| Guide | Covers |
|---|---|
| [Git workflow](git-workflow.md) | Branches, Conventional Commits, GPG + DCO signing, pull requests, reviews |
| [Terraform](terraform.md) | Module layout, version pinning, naming, tagging, workspaces, releases |
| [CI/CD](ci-cd.md) | Composite actions, required checks, reusable workflows, pinning actions |
| [Security](security.md) | Secrets, least-privilege IAM, scanning, dependency hygiene |
| [Documentation](documentation.md) | READMEs, `.header.md`, terraform-docs, where docs live |
| [AI-assisted development](ai-assisted-development.md) | Using Claude and custom agents safely |

## Principles

1. **Everything as code, everything reviewed.** No manual console changes. If an emergency
   change is made by hand, it is back-ported to code within one working day.
2. **Fix at the lowest layer.** See the [Repository Guide](../repository-guide.md).
3. **Pin everything.** Terraform, providers, modules, Actions, container base images.
4. **Fast local feedback.** The same checks run in `pre-commit` and in CI; CI should never be the first place a problem is found.
5. **Least privilege by default.** Grant the smallest permission that works, and scope it.
6. **Leave it documented.** A change is not done until its README and this guide are current.

## Changing these practices

These guides are owned by the whole organisation.

1. Start a thread in [Discussions → Best Practices](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions)
   using the *Best practice proposal* template.
2. Once there is rough consensus, open a PR here that links the discussion.
3. A PR changing a practice needs approval from at least two platform maintainers.
4. Announce the change in the discussion and update affected repositories (or open issues to track it).
