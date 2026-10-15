# Suleiman Abdulrahman

Cloud & DevOps engineer · Remote (UTC+1)

[suleiman.abdulrahman.dev@gmail.com](mailto:suleiman.abdulrahman.dev@gmail.com) ·
[LinkedIn](https://linkedin.com/in/suleiman-abdulrahman-dev) ·
[Dev.to](https://dev.to/cypher682)

---

## About

I'm a KCNA-certified cloud and DevOps engineer with about 1.5 years of hands-on AWS work. I like
infrastructure that is written as code, delivered through GitOps, secure by default, and
observable from the start. I came to this from software development, so I'm comfortable on both
sides of the application/infrastructure line.

Most of the projects below are self-directed: I build a system end to end, run it, and then write
down what actually happened. Each README says plainly what is verified, what is simulated, and
what is still missing — including where something only runs locally.

## What I'm building now

### Vortex — embedded finance for small businesses *(private)*

My main current project. It's proprietary, so there's no link here, but I'm happy to walk through
the architecture on a call.

- A two-layer fintech product: an embedded-finance core (multi-tenant wallets, internal
  transfers, payouts, a double-entry append-only ledger) with SMB financial operations on top —
  invoicing, expenses, subscription billing, a VAT/WHT tax engine, bank reconciliation, KYC/KYB
  tiers, outbound webhooks and a developer portal.
- Python 3.12 and FastAPI over PostgreSQL 16, Redis and Kafka, with a Next.js dashboard. Built as
  a modular monolith, so a module can be split into a service later without a rewrite.
- Money correctness is treated as a hard requirement: integer minor-unit amounts, row-level
  security enforced by a non-superuser database role, idempotency keys on every money move, and
  64 tracked Alembic migrations.
- 85 architecture decision records, 700+ backend tests, and CI across three stacks — `ruff` and
  pytest for Python, `tsc`/vitest/`next build` for TypeScript, and Terraform, Helm, Checkov and
  Trivy for infrastructure.

## What I work with

| | |
|---|---|
| **Cloud & IaC** | AWS (VPC, EC2/ASG, ALB, RDS, ECS Fargate, ECR, S3, IAM, SSM, Lambda, EventBridge, CloudWatch), Terraform, Ansible |
| **Containers & delivery** | Docker, Kubernetes, Helm, Argo CD, Argo Rollouts, GitHub Actions (OIDC), GitLab CI |
| **Security** | Trivy, Checkov, Cosign, SOPS + age, OPA Gatekeeper, CIS benchmarks, least-privilege IAM |
| **Observability** | Prometheus, Grafana, Loki, Tempo, Jaeger, OpenTelemetry, Alertmanager, SLO alerts |
| **Languages** | Python, Go, Bash, TypeScript, SQL, Linux |

---

## Selected projects

### [gitops-pipeline](https://github.com/cypher682/gitops-pipeline)

- GitLab CI commits desired state to Git and Argo CD reconciles it, so a rollback is a git revert.
  One ApplicationSet template generates the dev and staging environments.
- Argo Rollouts shifts traffic 10% → 50% → 100% and aborts automatically if the Prometheus error
  rate passes 5%. Ran 22/22 pipeline jobs green on a local Kubernetes cluster.
- Cosign keyless signing and SOPS + age encrypted secrets.

`GitLab CI` `Argo CD` `Argo Rollouts` `Kubernetes` `Helm` `Cosign` `SOPS`

### [infra-core](https://github.com/cypher682/infra-core)

- 79 AWS resources provisioned with modular Terraform across two environments (2-tier, 2-AZ VPC,
  ALB, EC2 Auto Scaling, RDS, ECR, IAM, CloudWatch), verified end to end then destroyed to keep
  costs down.
- No inbound SSH: private subnets, IMDSv2, admin access only through SSM Session Manager, with
  GuardDuty, Security Hub (CIS v1.4) and AWS Config as a baseline.
- Pull requests run a Terraform plan behind a Checkov gate; merges apply, run 50 idempotent
  Ansible hardening tasks and smoke-test the ALB — authenticating with GitHub OIDC, no stored keys.

`AWS` `Terraform` `Ansible` `SSM` `GitHub Actions OIDC` `Checkov`

### [nexuspay-platform](https://github.com/cypher682/nexuspay-platform)

- Four TypeScript services (gateway, auth, payments, notifications) behind one public entrypoint,
  delivered with a Helm library chart, an Argo CD ApplicationSet and Gatekeeper policies.
- Payments are idempotent with a double-entry ledger in integer minor units; k6 load testing found
  three real bugs, including synchronous bcrypt blocking the event loop.
- Runs locally on Docker Compose and minikube — not deployed to a cloud cluster, and the payment
  and email/SMS providers are simulated behind clean interfaces so the stack works offline.

`TypeScript` `Express 5` `PostgreSQL` `Redis` `RabbitMQ` `Kubernetes` `Helm` `Argo CD` `k6`

### [cloudguard-pro](https://github.com/cypher682/cloudguard-pro)

- CloudTrail → EventBridge → Lambda. Seven Python functions remediate misconfigurations in under
  a minute: revoking 0.0.0.0/0 SSH and RDP rules, re-enabling S3 Block Public Access, and removing
  console logins for IAM users without MFA — verified against a live account.
- 70 tests at 87% coverage behind an 80% CI gate, with Bandit and Checkov in the pipeline.

`Python` `AWS Lambda` `EventBridge` `DynamoDB` `Terraform` `Pulumi`

### [observability-platform](https://github.com/cypher682/observability-platform)

- Prometheus, Loki, Tempo, Grafana, Alertmanager and an OpenTelemetry Collector across 14 Docker
  Compose services, with trace-to-log correlation and alert inhibition backed by per-alert runbooks.
- Seven Grafana dashboards provisioned as code, plus a custom Python Prometheus exporter.

`Prometheus` `Grafana` `Loki` `Tempo` `OpenTelemetry` `Alertmanager` `Python`

### [ecs-production-platform](https://github.com/cypher682/ecs-production-platform)

- A 2-AZ VPC, ALB, ECS Fargate service, private RDS PostgreSQL, ECR, ACM and Route 53, all in
  Terraform, with ALB weighted target groups for zero-downtime blue-green cutover and a rollback
  that is the same command.
- Credentials in SSM Parameter Store, deploys over OIDC. No NAT Gateway (about $33/month avoided);
  the live validation cost roughly $0.50.

`Terraform` `AWS ECS Fargate` `ALB` `RDS` `Route 53` `ACM`

### [platform-cli](https://github.com/cypher682/platform-cli)

- Cobra CLI on the Docker SDK, using goroutines and channels for concurrent health checks and log
  tailing, plus environment lifecycle, migrations and service scaffolding.
- CI runs vet and unit tests across 8 packages; goreleaser is wired for releases on version tags,
  though there is no tagged release yet.

`Go` `Cobra` `Docker SDK` `GitHub Actions`

**Also on GitHub:** [aws-cost-security-auditor](https://github.com/cypher682/aws-cost-security-auditor)
(read-only AWS audit CLI, 32 findings on a live account) ·
[vpcctl-linux-networking](https://github.com/cypher682/vpcctl-linux-networking)
(VPC rebuilt with Linux network namespaces and iptables)

---

## Experience

**DevOps intern — Emerj LLC (HNG13 DevOps track)** · Sep 2025 – Dec 2025
Supported production deployments for two live products, one of them shipping to the Play Store and
App Store. Rebuilt CI/CD with GitHub Actions across four environments on one product; diagnosed an
nginx misconfiguration that routed production traffic to the wrong product and migrated to a
dedicated server (systemd, PM2, nginx, Let's Encrypt); handled remote redeploys and moved server
config and data with rsync during a provider transition.

**Software developer (national service) — Securities and Exchange Commission** · Jul 2025 – May 2026
Enterprise Architecture & Innovation Division. Set up Oracle Enterprise Suite portal access for the
HR, tax and finance offices; wrote Python scripts to replace recurring manual Excel processing;
built components for internal HR and staff portals on Oracle APEX; contributed the Svelte frontend
for a live public investor-portal feature, adding bot protection against the existing PHP codebase.

---

## Certification

**Kubernetes and Cloud Native Associate (KCNA)**, CNCF · July 2026 · ID `LF-spu35j7v73`

Self-paced: Linux Foundation LFS101 and LFS158; AWS Cloud Practitioner, Solutions Architect and
DevOps Engineer coursework. I write up what I build on [Dev.to](https://dev.to/cypher682).

<sub>B.Sc. Computer Science, Ahmadu Bello University · 2024</sub>
