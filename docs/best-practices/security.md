# Security

## Secrets

- **Never commit secrets**, credentials, private keys, kubeconfigs or state files. `pre-commit`
  runs secret detection; keep `.secrets.baseline` up to date rather than disabling the hook.
- Store runtime secrets in AWS Secrets Manager / Vault and reference them (e.g. External Secrets Operator).
- CI uses OIDC roles, not access keys. Personal access tokens are short-lived and least-scoped.
- If a secret leaks: **rotate first**, then clean history, then report (see [SECURITY.md](../../SECURITY.md)).

## IAM — least privilege

- No `"Action": "*"` or `"Resource": "*"` without a written justification in the PR.
- Scope by resource ARN and add `Condition` blocks (`aws:SourceAccount`, `aws:PrincipalTag`, OIDC `sub`).
- Workloads use **IRSA / EKS Pod Identity**, never node-role permissions.
- Roles and policies follow `rol-*` / `pol-*` naming and `/hxmin-cloud/...` paths (see [Terraform](terraform.md)).
- Use the `iam-policy-reviewer` agent before merging IAM changes.

## Network

- Private subnets for data planes and workloads; public only for load balancers / NAT.
- Security groups allow the minimum ports from referenced security groups, not wide CIDRs.
- No `0.0.0.0/0` ingress except on public load balancers on 443.

## Data

- Encryption at rest (KMS) and in transit (TLS) on by default.
- S3: block public access, enforce TLS, versioning on state and data buckets.
- Deletion protection / `prevent_destroy` on stateful production resources.

## Scanning and dependencies

- Trivy (IaC + images) runs on every PR and nightly; fix HIGH/CRITICAL before merge.
  Suppressions go in `.trivyignore` **with a reason and expiry**.
- Pin and regularly update providers, modules, base images and Actions.
- Container images: minimal base, non-root user, no build secrets in layers.

## Access

- Access is granted to **teams**, never individuals, via `github-org-platform-governance`.
- Require 2FA and SSO; review team membership quarterly.
