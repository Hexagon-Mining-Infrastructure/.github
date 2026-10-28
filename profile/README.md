# Hexagon Mining Infrastructure

Home of the **Cloud Platform Deployment Stream (CPDS)**: the infrastructure-as-code,
platform tooling and engineering knowledge behind Hexagon Mining's cloud platform.

> **New here?** Start with the [Repository Guide](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/repository-guide.md)
> to find the right repository, then read the [Engineering Best Practices](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/best-practices/README.md).

---

## Where do I go?

| I want to… | Go to |
|---|---|
| Add or change a **reusable AWS building block** (VPC, IAM, RDS, S3, EKS…) | `terraform-aws-*` |
| Change how **HxMIN platform components** are composed (mgmt cluster, environments, datalake) | `terraform-hxmin-*` |
| **Deploy or change** a real environment / workspace | `terraform-live-*` |
| Change a **Kubernetes workload** chart or its per-environment values | `helm-charts` / `helm-values` |
| Change **CI/CD steps** shared by Terraform repos | `terraform-composite-actions` |
| Build or update **bastion AMIs** | `packer-bastion-images` |
| Build **container images** | `dockerfiles` |
| Read or write **platform documentation** | `wiki-infra-docs` |
| Change **org-wide rules**, repo settings or governance | `github-org-platform-governance` |
| Propose or discuss a **best practice** | [Discussions](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions) |

The full map, with how the layers depend on each other, is in the
[Repository Guide](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/docs/repository-guide.md).

## How we work

- **Everything as code.** No click-ops; every change goes through a pull request.
- **Small, layered modules.** Generic `terraform-aws-*` → opinionated `terraform-hxmin-*` → deployed `terraform-live-*`.
- **Conventional Commits, signed.** `type(scope): subject`, GPG-signed with a DCO `Signed-off-by` trailer.
- **Pinned versions.** Every module, provider and action is pinned. No floating refs.
- **Shift-left quality.** `pre-commit`, `tflint`, `trivy` and secret scanning run locally *and* in CI.

## Getting help

- Questions and ideas → [Discussions](https://github.com/orgs/Hexagon-Mining-Infrastructure/discussions)
- Bugs in a specific repo → open an issue in that repo
- Security issues → see [SECURITY.md](https://github.com/Hexagon-Mining-Infrastructure/.github/blob/main/SECURITY.md) (never a public issue)
