<h1 align="center">Suleiman Abdulrahman (Cypher)</h1>
<h3 align="center">Cloud Infrastructure, DevOps & Platform Engineer</h3>

<p align="center">
  Designing, automating, and operating production-grade cloud systems across AWS & Kubernetes — built for security, observability, and resilience.
</p>

<p align="center">
  <a href="https://github.com/cypher682"><img src="https://img.shields.io/badge/GitHub-cypher682-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
  <a href="https://linkedin.com/in/suleiman-abdulrahman-dev"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="mailto:suleiman.abdulrahman.dev@gmail.com"><img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>

---

## 🚀 Core Engineering Focus

- **Cloud Infrastructure & IaC:** Multi-environment AWS infrastructure (VPC, EC2 ASG, ALB, RDS, ECS Fargate), Terraform modules, Pulumi, Ansible configuration management.
- **Cloud Security & Compliance:** Event-driven automated security remediation, CIS AWS Foundations Benchmarks, GuardDuty, Security Hub, AWS Config, zero-open-port SSM architecture.
- **Observability & Telemetry:** Full LGTM stack (Loki, Grafana, Tempo, Prometheus), OpenTelemetry Collector pipelines, custom Prometheus exporters, trace-to-log correlation, dashboards-as-code.
- **CI/CD & Software Engineering:** OIDC role federation pipelines (GitHub Actions), containerized backend microservices in Python (FastAPI) and Node.js/TypeScript (BullMQ, Redis, WebSockets).

---

## 📦 Featured Portfolio Projects

### 🔹 [infra-core](https://github.com/cypher682/infra-core)
Production-grade AWS infrastructure platform provisioned with modular Terraform, hardened with Ansible, and delivered through a GitHub Actions OIDC pipeline.

- 2-tier VPC (Public/Private), ALB, EC2 ASG, RDS PostgreSQL, GuardDuty, Security Hub, AWS Config.
- Zero SSH ports open — full operational management via AWS SSM Session Manager.
- Checkov IaC security scanning & automated HTTP ALB smoke testing on deployment.

`Terraform` `Ansible` `AWS` `SSM` `GuardDuty` `GitHub Actions (OIDC)`

---

### 🔹 [cloudguard-pro](https://github.com/cypher682/cloudguard-pro)
Event-driven AWS security platform that detects and automatically remediates cloud misconfigurations in real time.

- Real-time API event interception via CloudTrail → EventBridge → 7 Python Lambda remediators.
- Auto-revokes open SSH rules (60s), deletes console access for non-MFA users (30s), restores S3 public access blocks.
- Dual IaC architecture: Terraform for static infrastructure, Pulumi (Python) for compute & Lambda layers.

`Python` `AWS Lambda` `EventBridge` `DynamoDB Streams` `Terraform` `Pulumi` `SNS`

---

### 🔹 [observability-platform](https://github.com/cypher682/observability-platform)
Standalone, vendor-neutral LGTM observability pipeline built from scratch to correlate metrics, logs, and traces.

- OpenTelemetry Collector routing traces to Tempo, metrics to Prometheus, and logs to Loki.
- Loki `derivedFields` mapping log `trace_id` directly to Tempo trace waterfalls.
- Custom Python Prometheus exporter & 7 Grafana dashboards provisioned as code.

`Prometheus` `Loki` `Tempo` `Grafana` `OpenTelemetry` `Docker Compose` `Kubernetes`

---

### 🔹 [authcore-service](https://github.com/cypher682/authcore-service)
Production-grade IAM service implementing secure authentication, authorization, and tenant isolation.

- OAuth2 with PKCE, TOTP 2FA/MFA, AES-256 encrypted refresh token rotation, and RBAC permissions.
- Redis-backed rate limiting, brute-force IP throttling, and audit logging.
- Fully tested Python FastAPI architecture with Docker containerization and CI/CD.

`FastAPI` `Python` `PostgreSQL` `Redis` `OAuth2` `Docker` `pytest`

---

### 🔹 [nodeflow-api](https://github.com/cypher682/nodeflow-api)
High-throughput asynchronous webhook delivery & workflow engine engineered for reliability under high concurrency.

- BullMQ & Redis distributed task queues with exponential backoff retries & dead-letter queue (DLQ).
- HMAC SHA-256 signature verification, circuit breaker pattern, and real-time WebSocket job updates.
- TypeScript architecture with PostgreSQL transaction management and health monitoring.

`Node.js` `TypeScript` `BullMQ` `Redis` `PostgreSQL` `WebSockets`

---

### 🔹 [ecs-production-platform](https://github.com/cypher682/ecs-production-platform)
Production container platform built on AWS ECS Fargate featuring blue-green zero-downtime deployments.

- Modular Terraform managing 36+ resources across VPC, ALB, ECS Fargate, and RDS PostgreSQL.
- ALB target group weighting for zero-downtime deployment switches and instant automated rollbacks.
- Verified live AWS sprint evidence with full SSL certificate termination (ACM) and Route 53 DNS.

`Terraform` `AWS ECS Fargate` `ALB` `RDS` `Route 53` `ACM`

---

## 🛠️ Technical Skill Matrix

| Domain | Technologies & Tools |
|---|---|
| **Cloud Platforms** | AWS (VPC, EC2, ECS Fargate, RDS, S3, IAM, SSM, CloudTrail, GuardDuty, Security Hub, Config), Azure |
| **Infrastructure as Code** | Terraform (Modular Architecture, Remote State), Pulumi (Python), CloudFormation |
| **Containers & Orchestration** | Docker, Docker Compose, Kubernetes, Helm, Istio, ArgoCD |
| **CI/CD & Automation** | GitHub Actions (OIDC Federation, SAST, Checkov), Ansible (Hardening, Playbooks) |
| **Observability & Logging** | Prometheus, Grafana, Loki, Tempo, OpenTelemetry Collector, Promtail, Alertmanager, CloudWatch |
| **Software & Systems** | Python (FastAPI, boto3), Node.js / TypeScript (Express, BullMQ), Go, Bash, Linux Systems (`proc`, namespaces, `iptables`) |

---

## 📊 GitHub Analytics

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=cypher682&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="150" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=cypher682&layout=compact&theme=tokyonight&hide_border=true" height="150" />
</p>
