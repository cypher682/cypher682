# Suleiman Abdulrahman

Cloud & DevOps engineer · Remote (UTC+1) ·
[suleiman.abdulrahman.dev@gmail.com](mailto:suleiman.abdulrahman.dev@gmail.com) ·
[LinkedIn](https://linkedin.com/in/suleiman-abdulrahman-dev) ·
[Dev.to](https://dev.to/cypher682)

I build cloud and platform systems end to end — infrastructure as code, GitOps delivery, and the
security and observability around them. Many of the repos below have a write-up that goes through
the design decisions and what actually happened, including the parts that didn't work first time.

---

## Currently building

### Vortex — embedded finance for small businesses *(private)*

An embedded-finance core (multi-tenant wallets, internal transfers, payouts, a double-entry
append-only ledger) with SMB financial operations on top: invoicing, expenses, subscription
billing, a VAT/WHT tax engine, bank reconciliation, KYC/KYB tiers, outbound webhooks and a
developer portal.

Python 3.12 / FastAPI on PostgreSQL, Redis and Kafka, with a Next.js dashboard. Built as a modular
monolith, with integer minor-unit money, row-level security enforced by a non-superuser database
role, idempotency keys on every money move, 64 migrations, 85 design records and 700+ backend
tests under CI.

The repo is proprietary so there's no link here — I'm happy to walk through the architecture on a
call.

---

## Projects

### [gitops-pipeline](https://github.com/cypher682/gitops-pipeline)

GitOps delivery with a Prometheus-gated canary. GitLab CI commits desired state to Git and Argo CD
reconciles it, so a rollback is a git revert; Argo Rollouts shifts traffic 10% → 50% → 100% and
aborts automatically above a 5% error rate. Images are Cosign keyless signed and secrets are
SOPS + age encrypted. 22/22 pipeline jobs green on a local cluster.

`GitLab CI` `Argo CD` `Argo Rollouts` `Kubernetes` `Helm` `Cosign` `SOPS`
→ [Canaries, keyless signing and Prometheus gates](https://dev.to/cypher682/building-a-real-gitops-pipeline-argo-cd-canaries-cosign-keyless-signing-and-prometheus-gates-1o2i)

### [infra-core](https://github.com/cypher682/infra-core)

A multi-environment AWS platform in Terraform and Ansible: 79 resources across two environments
(2-tier, 2-AZ VPC, ALB, EC2 Auto Scaling, RDS, ECR, IAM, CloudWatch), verified end to end then
destroyed to keep costs down. No inbound SSH — private subnets, IMDSv2, admin access only through
SSM Session Manager — with GuardDuty, Security Hub and AWS Config as a baseline. Pull requests run
a Terraform plan behind a Checkov gate; merges apply, run 50 idempotent hardening tasks and
smoke-test the ALB, authenticating with GitHub OIDC.

`AWS` `Terraform` `Ansible` `SSM` `GitHub Actions OIDC` `Checkov`
→ [Modular AWS infrastructure, CIS-hardened EC2 and OIDC CI/CD](https://dev.to/cypher682/modular-aws-infrastructure-with-terraform-2-tier-vpc-cis-hardened-ec2-oidc-cicd-and-a-6-bkj)

### [cloudguard-pro](https://github.com/cypher682/cloudguard-pro)

Event-driven AWS security remediation: CloudTrail → EventBridge → Lambda. Seven Python functions
fix misconfigurations in under a minute — revoking 0.0.0.0/0 SSH and RDP rules, re-enabling S3
Block Public Access, removing console logins for IAM users without MFA — verified against a live
account. 70 tests at 87% coverage behind an 80% CI gate, with Bandit and Checkov in the pipeline.

`Python` `AWS Lambda` `EventBridge` `DynamoDB` `Terraform` `Pulumi`
→ [Event-driven AWS security automation](https://dev.to/cypher682/event-driven-aws-security-automation-real-time-detection-and-remediation-with-terraform-and-pulumi-1jod)

### [observability-platform](https://github.com/cypher682/observability-platform)

A vendor-neutral LGTM stack: Prometheus, Loki, Tempo, Grafana, Alertmanager and an OpenTelemetry
Collector across 14 Docker Compose services, with trace-to-log correlation and alert inhibition
backed by per-alert runbooks. Seven dashboards provisioned as code, plus a custom Python
Prometheus exporter.

`Prometheus` `Grafana` `Loki` `Tempo` `OpenTelemetry` `Alertmanager`
→ [Building the full LGTM stack from scratch](https://dev.to/cypher682/building-the-full-lgtm-observability-stack-from-scratch-metrics-logs-traces-and-alerting-2l9f)

### [ecs-production-platform](https://github.com/cypher682/ecs-production-platform)

Blue-green containers on ECS Fargate: a 2-AZ VPC, ALB, Fargate service, private RDS PostgreSQL,
ECR, ACM and Route 53, all in Terraform, with weighted target groups for zero-downtime cutover and
a rollback that is the same command. Credentials in SSM Parameter Store, deploys over OIDC, no NAT
Gateway (about $33/month avoided). The live validation cost roughly $0.50.

`Terraform` `AWS ECS Fargate` `ALB` `RDS` `Route 53`
→ [Designing a blue-green ECS platform on AWS](https://dev.to/cypher682/designing-a-production-grade-blue-green-ecs-platform-on-aws-with-terraform-2n5h)

### [nexuspay-platform](https://github.com/cypher682/nexuspay-platform)

Four TypeScript services (gateway, auth, payments, notifications) behind a single public
entrypoint, delivered with a Helm library chart, an Argo CD ApplicationSet and Gatekeeper policies
for allowed registries, required resources and non-root containers. Payments are idempotent with a
double-entry ledger in integer minor units. k6 load testing found three real bugs, including
synchronous bcrypt blocking the event loop. Runs locally on Docker Compose and minikube — not
deployed to a cloud cluster, and the payment and email/SMS providers are simulated behind clean
interfaces so the stack works offline.

`TypeScript` `Express 5` `PostgreSQL` `Redis` `RabbitMQ` `Kubernetes` `Helm` `Argo CD` `k6`

### [authcore-service](https://github.com/cypher682/authcore-service)

An IAM service in FastAPI: JWT access tokens with refresh-token rotation and family-level reuse
detection, TOTP MFA, session management with device fingerprints, dynamic RBAC, audit logs, and
Redis-backed brute-force lockout. PostgreSQL and Redis with Celery for background work and Alembic
migrations. The pytest suite runs against real Postgres and Redis at 81% coverage, and CI runs
lint → test → Docker build → Trivy scan.

`FastAPI` `JWT` `TOTP` `PostgreSQL` `Redis` `Celery` `Docker`
→ [Building an IAM service with FastAPI](https://dev.to/cypher682/building-an-iam-service-with-fastapi-refresh-token-families-totp-mfa-and-rbac-gc4)

### [nodeflow-api](https://github.com/cypher682/nodeflow-api)

An asynchronous job orchestration and webhook delivery API with a two-process architecture — an
Express API and a separate BullMQ worker — so retries, delayed jobs, priorities and dead-letter
queues are handled off the request path. Webhooks are HMAC-SHA256 signed, and a Redis emitter lets
the worker push job updates to WebSocket clients without either process knowing about the other.
31 tests across 7 suites.

`Node.js` `TypeScript` `BullMQ` `Redis` `PostgreSQL` `WebSockets`
→ [Building an async job platform with BullMQ and webhooks](https://dev.to/cypher682/building-an-async-job-platform-with-bullmq-socketio-and-webhooks-2m55)

---

## Polyglot systems

Newer work built outside the Node.js and Python stacks: the same domain problems taken on in Go,
Rust and Java, plus one ML control plane. All of them run locally on Docker Compose — none is
deployed — and each README states what it does and does not do yet, including the work that is
still missing.

### Go

**[distro](https://github.com/cypher682/distro)** — a multi-tenant distributor and wholesale
platform: catalogue and pricing, purchase orders and receiving, append-only stock movements and
reservations, the order lifecycle through picking, dispatch and invoicing, weighted-average costing
and cost of goods sold, sales returns, and a double-entry ledger, with an authenticated console on
top. Tenant isolation is enforced by PostgreSQL row-level security rather than application filters.
9.9k lines of Go, with unit, HTTP and PostgreSQL concurrency checks in the suite and
`go test` / `vet` / `build` in CI.

`Go` `PostgreSQL` `Row-Level Security` `Docker Compose`

**[inventory-fulfillment-control](https://github.com/cypher682/inventory-fulfillment-control)** —
a high-scale inventory control plane. A reservation is one conditional `UPDATE`, so concurrent
orders cannot oversell; costing runs on FIFO layers posting to a reconcilable sub-ledger; transfers
move quantity and value between locations through in-transit; lot/serial tracking and quality holds
keep stock on hand while removing it from ATP and from FIFO consumption. Events and a transactional
outbox are written in the same transaction, with a replay verifier and a load harness that reports
percentiles. Stages 0–10 complete, 7.7k lines of Go.

`Go` `PostgreSQL` `NATS JetStream` `Prometheus` `Transactional Outbox`

**[programmable-b2b-commerce](https://github.com/cypher682/programmable-b2b-commerce)** —
commercial contracts that execute as auditable workflows across organisational boundaries: versioned
drafts with immutable history, a lifecycle state machine, and deterministic pricing evaluated
against the active version, with commitment-coverage reporting and evaluation records that carry
input and result hashes. Two of eight stages are built — reservation under concurrency, the saga
layer and ledger integration are still ahead.

`Go` `PostgreSQL` `Docker Compose`

**[order-to-cash-settlement](https://github.com/cypher682/order-to-cash-settlement)** — multi-entity
order-to-cash with multilateral netting and verifiable settlement receipts. This one is the
scaffold: service skeleton, environment configuration, health endpoint and a build that runs. The
reservation core, ledger and settlement engine are not written yet, and the README tracks them
stage by stage.

`Go` `PostgreSQL`

### Rust

**[attest](https://github.com/cypher682/attest)** — a credential and verification network:
institutions issue signed credentials, holders get a share link and QR code, and anyone can verify
them online or offline. Ed25519 issuer keys with rotation and explicit key revocation, per-issuer
credential schemas, idempotent bulk issuance, status-list revocation, and a SHA-256 Merkle
transparency log with inclusion and consistency proofs. The offline verifier is its own CLI, so a
credential can be checked without trusting the issuer's server.

`Rust` `Ed25519` `Merkle Transparency Log` `PostgreSQL`

**[credential-audit-mesh](https://github.com/cypher682/credential-audit-mesh)** — the same problem
taken further into auditability: deterministic Ed25519 verification over HTTP, an append-only
transparency log with signed tree heads and prefix-consistency proofs, and a browser console that
verifies inclusion client-side instead of trusting the API. Revocation, selective disclosure and
the authorization engine are still to come.

`Rust` `Ed25519` `Transparency Log` `Docker Compose`

### Java

**[meridian](https://github.com/cypher682/meridian)** — a clinic and lab workspace: patient
registration and search, encounters, lab orders through sample collection, result entry and
release, amendments that keep the previous value and the reason for the change, HL7 v2 `ORU^R01`
ingestion from a lab analyser, a small FHIR R4 facade, visit invoicing, pharmacy stock and
dispenses, and a facility-scoped hash-chained audit log whose chain can be verified. Front-desk and
billing changes queue while the API is down and replay idempotently. Spring Boot with Keycloak for
auth, and a README that says plainly it is a local demo with demo authentication and no real
patient data.

`Java` `Spring Boot` `PostgreSQL` `HL7 v2` `FHIR R4` `Keycloak`

### Go + Python

**[autonomous-allocation-control-plane](https://github.com/cypher682/autonomous-allocation-control-plane)**
— the one ML system here, and shaped so the model cannot move stock on its own. A Python demand
service returns p50/p90 forecasts and proposals; a Go control plane re-checks model status,
confidence, drift, quantity caps and source-stock floors before anything executes; execution is a
single Postgres transaction covering the position change, ledger rows, the decision record, an
event and an outbox row. Models move candidate → shadow → promoted through gates on WAPE, p90
coverage, sample size and non-inferiority instead of deploying automatically, and a rollback posts
compensating ledger entries. The suite drives 250 concurrent reservations against the same stock
and checks it never goes negative; `docs/VERIFICATION.md` records the demo output and the results.

`Go` `Python` `PostgreSQL` `Docker Compose` `ML promotion gates`

---

## Smaller projects

- [platform-cli](https://github.com/cypher682/platform-cli) — Go CLI for local platform tasks:
  Cobra on the Docker SDK, goroutines and channels for concurrent health checks and log tailing,
  plus environment lifecycle, migrations and scaffolding. 8 packages under CI.
- [aws-cost-security-auditor](https://github.com/cypher682/aws-cost-security-auditor) — read-only
  AWS audit CLI; 32 findings across IAM, EC2, EBS and S3 on a live account.
  → [write-up](https://dev.to/cypher682/building-a-production-grade-aws-cost-security-auditor-nb1)
- [vpcctl-linux-networking](https://github.com/cypher682/vpcctl-linux-networking) — a VPC rebuilt
  locally with Linux network namespaces, veth pairs, bridges and iptables NAT.
  → [write-up](https://dev.to/cypher682/building-your-own-virtual-private-cloud-on-linux-a-deep-dive-into-network-namespaces-1l3e)
- [aws-microservices-cicd](https://github.com/cypher682/aws-microservices-cicd) — microservices
  platform with a Terraform and GitHub Actions pipeline on the AWS free tier.
  → [write-up](https://dev.to/cypher682/building-a-production-ready-microservices-platform-with-cicd-on-aws-free-tier-2la0)
- [polyglot-microservices-platform](https://github.com/cypher682/polyglot-microservices-platform) —
  five services in four languages (Go, Node.js, Java, Python) behind a Vue frontend, with Docker,
  Traefik and a Terraform + Ansible + GitHub Actions deployment.
  → [write-up](https://dev.to/cypher682/complete-beginners-guide-to-building-a-microservices-todo-application-with-docker-and-traefik-5gok)
- [hng13-stage-3-devops](https://github.com/cypher682/hng13-stage-3-devops) — blue-green deployment
  with Nginx failover and a log watcher that raises Slack alerts.
  → [write-up](https://dev.to/cypher682/complete-beginners-guide-to-blue-green-deployment-with-nginx-and-real-time-alerting-268c)
