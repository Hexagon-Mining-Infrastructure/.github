# Hexagon Mining Infrastructure: members

Welcome to the **Cloud Platform Deployment Stream (CPDS)**. Only organisation members can see
this page. The public overview is in the
[`.github` profile](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/profile/README.md).

> 🔒 This content is for members only. Internal details belong here or in a private repository,
> never in `.github` or any other public repository.

---

## Onboarding checklist

1. Read the [Repository Guide](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/repository-guide.md) to learn the three Terraform layers and which repo to use.
2. Read the [Engineering Best Practices](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/README.md), starting with [Git workflow](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/git-workflow.md) and [Terraform](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/terraform.md).
3. Set up **GPG commit signing** and add the DCO `Signed-off-by` trailer (`git commit -s -S`).
4. Install `pre-commit` and run `pre-commit install` in every repo you clone.
5. Read [AI-assisted development](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/ai-assisted-development.md) and try the custom agents below.

## Custom AI agents

Org-wide custom agents live in
[`.github-private/agents`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/tree/main/agents).
Any member can use them in Copilot coding agent. Claude Code subagent versions live in
[`.claude/agents`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/tree/main/.claude/agents).

| Agent | Use it to… |
|---|---|
| [`infrastructure-standards`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/infrastructure-standards.md) | Get guidance on CPDS infrastructure standards, tooling and best practices |
| [`implementation-planning`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/implementation-planning.md) | Create implementation plans with several approaches and test cases |
| [`critical-code-reviewer`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/critical-code-reviewer.md) | Review repos, branches and PRs, then document issues in priority order |
| [`commit-push-assistant`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/commit-push-assistant.md) | Stage, commit and push changes safely |
| [`devops-documentation-writer`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/devops-documentation-writer.md) | Write and maintain CPDS DevOps docs, runbooks and architecture guides based on what's actually in the repos |
| [`documentation-retrieval`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/documentation-retrieval.md) | Fetch and analyse docs from Jira, Confluence, GitHub Wiki and repositories |
| [`jira-ticket-creator`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/jira-ticket-creator.md) | Write detailed Jira tickets with acceptance criteria |
| [`jira-ticket-specialists`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/jira-ticket-specialists.md) | Coordinate Jira ticket creation and GitHub integration |
| [`github-issue-creator`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/github-issue-creator.md) | Create GitHub issues |
| [`github-jira-linker`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/github-jira-linker.md) | Link Jira tickets and GitHub issues to each other |
| [`custom-agent-creator`](https://github.com/Hexagon-Mining-Infrastructure/.github-private/blob/main/agents/custom-agent-creator.md) | Create a new custom agent |

You can add or change an agent with a pull request to `.github-private`. See
[Creating custom agents](https://docs.github.com/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents).

## Day-to-day

- **Plan work** in Jira. Put the ticket key in your branch name (`feature/CPDS-123-…`) and in your PR.
- **Change infrastructure** with a PR to the right `terraform-*` repo. Never use click-ops.
- **Ask for review** with the PR template. Repos that have enabled the shared Claude PR review
  workflow review PRs automatically. See
  [AI-assisted development](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/ai-assisted-development.md).

## Getting help

- Questions and ideas → [Discussions](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions)
- Bugs in a specific repo → open an issue in that repo
- Security issues → follow [SECURITY.md](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/SECURITY.md) privately and never in a public issue
