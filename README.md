# .github

Organisation-level repository for **Hexagon Mining Infrastructure**.

| Path | Purpose |
|---|---|
| [`profile/README.md`](profile/README.md) | Org landing page shown on github.com/Hexagon-Mining-Infrastructure |
| [`docs/repository-guide.md`](docs/repository-guide.md) | Map of every repo and how to choose where a change goes |
| [`docs/best-practices/`](docs/best-practices/README.md) | Org-wide engineering standards |
| [`CONTRIBUTING.md`](CONTRIBUTING.md), [`SECURITY.md`](SECURITY.md), [`SUPPORT.md`](SUPPORT.md), [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Default community health files for every repo without its own |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE), [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Default issue and PR templates |
| [`.github/DISCUSSION_TEMPLATE/`](.github/DISCUSSION_TEMPLATE) | Templates for org Discussions (best-practice proposals) |

## How defaults work

GitHub uses a file from this repository whenever a repository in the org doesn't have its own
copy (`CONTRIBUTING.md`, `SECURITY.md`, issue/PR templates, …). A repository overrides a default
simply by adding its own file.

> ⚠️ This repository is **public**. Don't add internal hostnames, account IDs, credentials or
> customer information. Member-only content belongs in `.github-private`.

## Contributing

Changes to practices follow the process in
[docs/best-practices/README.md](docs/best-practices/README.md#changing-these-practices).
