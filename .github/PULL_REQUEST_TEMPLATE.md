<!--
PR title must be a Conventional Commit, e.g. "feat(mgmt-eks): enable imdsv2 on node groups"
Jira: include CPDS-XXX in the title or below.
-->

## What

<!-- What does this change do? -->

## Why

<!-- Problem / motivation. Link the Jira issue: CPDS-XXX -->

## How it was tested

<!-- Commands run, examples/tests, environments. For live repos paste or link the plan. -->

<details><summary>terraform plan (live repos)</summary>

```text

```

</details>

## Risk and rollout

<!-- Breaking change? Resources replaced/destroyed? Rollback plan? Dependent PRs (bottom-up order)? -->

## Checklist

- [ ] Correct repository/layer (see the [Repository Guide](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/repository-guide.md))
- [ ] Commits are Conventional, GPG-signed and DCO signed-off
- [ ] `pre-commit run --all-files` passes locally
- [ ] Versions pinned; tags and naming follow standards
- [ ] Docs updated (`.header.md` / README / `UPGRADE-x.0.md` if breaking)
- [ ] No secrets, account IDs or credentials in the diff
