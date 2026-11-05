# Security

## Secrets

- **Never commit secrets**, credentials, private keys, cluster credentials or state files. Local
  checks run secret detection; keep the baseline up to date rather than disabling the hook.
- Store runtime secrets in a managed secret store and reference them, never inline them.
- CI uses short-lived federated credentials, not access keys. Personal access tokens are short-lived and least-scoped.
- If a secret leaks: **rotate first**, then clean history, then report (see [SECURITY.md](../../SECURITY.md)).

## Least privilege

- No wildcard actions or resources without a written justification in the PR.
- Scope permissions to specific resources and add conditions where supported.
- Workloads use their own scoped identities, never shared host-level permissions.
- Roles and policies follow the agreed naming conventions.

## Network

- Private networks for data planes and workloads; public only for load balancers / gateways.
- Firewall rules allow the minimum ports from referenced sources, not wide address ranges.
- No unrestricted ingress except on public load balancers on 443.

## Data

- Encryption at rest and in transit on by default.
- Storage: block public access, enforce TLS, versioning on state and data stores.
- Deletion protection on stateful production resources.

## Scanning and dependencies

- Security scanning (code + images) runs on every PR and nightly; fix HIGH/CRITICAL before merge.
  Suppressions are documented **with a reason and expiry**.
- Pin and regularly update dependencies, base images and CI actions.
- Container images: minimal base, non-root user, no build secrets in layers.

## Access

- Access is granted to **teams**, never individuals, and managed as code.
- Require 2FA and SSO; review team membership quarterly.
