# .github

Organisation-level repository for **Hexagon Mining Infrastructure**, home of the
**Hexagon Mining Deployment Platform**.

| Path | Purpose |
|---|---|
| [`profile/README.md`](profile/README.md) | Org landing page shown on github.com/Hexagon-Mining-Infrastructure |
| [`docs/best-practices/`](docs/best-practices/README.md) | Org-wide engineering standards for the Hexagon Mining Deployment Platform |
| [`CONTRIBUTING.md`](CONTRIBUTING.md), [`SECURITY.md`](SECURITY.md), [`SUPPORT.md`](SUPPORT.md), [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Default community health files for every repo without its own |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE), [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Default issue and PR templates |
| [`.github/DISCUSSION_TEMPLATE/`](.github/DISCUSSION_TEMPLATE) | Templates for org Discussions (best-practice proposals) |

## How defaults work

GitHub uses a file from this repository whenever a repository in the org doesn't have its own
copy (`CONTRIBUTING.md`, `SECURITY.md`, issue/PR templates, …). A repository overrides a default
simply by adding its own file.

> ⚠️ This repository is **public**. Don't add internal hostnames, account IDs, credentials,
> customer information, or details of the technologies and services we use.
> Member-only content belongs in `.github-private`.

## Contributing

Changes to practices follow the process in
[docs/best-practices/README.md](docs/best-practices/README.md#changing-these-practices).
