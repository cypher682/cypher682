<h1 align="center">Suleiman Abdulrahman (Cypher)</h1>

<h3 align="center">Cloud Infrastructure · DevOps · Platform Engineering</h3>

<p align="center">
  Building, automating, and operating cloud-native systems with a focus on infrastructure, security, observability, and reliability.
</p>

<p align="center">
  <a href="https://github.com/cypher682">
    <img src="https://img.shields.io/badge/GitHub-cypher682-181717?style=for-the-badge&logo=github&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/suleiman-abdulrahman-dev">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="mailto:suleiman.abdulrahman.dev@gmail.com">
    <img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
</p>

---

## About

I am a Cloud Infrastructure and DevOps Engineer focused on building systems that are **automated, secure, observable, and resilient**.

My work sits between infrastructure and software engineering — from provisioning AWS environments with Terraform and hardening Linux systems with Ansible, to deploying Kubernetes workloads through GitOps and building the backend systems those platforms operate.

My engineering focus includes:

- Cloud infrastructure and AWS architecture
- Infrastructure as Code and configuration management
- Kubernetes and platform engineering
- GitOps and progressive delivery
- Cloud security and DevSecOps
- Observability and SRE practices
- Distributed systems and asynchronous processing
- Backend engineering with Python and TypeScript

---

## Core Engineering Focus

### Cloud Infrastructure & IaC

- AWS infrastructure architecture and automation
- Multi-environment Terraform
- Modular infrastructure design
- Terraform remote state and state management
- Pulumi
- Ansible configuration management
- EC2, VPC, ALB, ASG, RDS, ECS Fargate
- AWS Systems Manager and private infrastructure
- IAM and least-privilege architecture

### Kubernetes & Platform Engineering

- Kubernetes cluster architecture and operations
- Helm
- ArgoCD
- Argo Rollouts
- GitOps
- Kubernetes resource management
- StatefulSets and DaemonSets
- OPA/Gatekeeper policy enforcement
- Containerized application platforms

### Security & DevSecOps

- AWS security architecture
- OIDC-based CI/CD authentication
- CIS Linux hardening
- GuardDuty, Security Hub, and AWS Config
- SOPS + AGE secrets management
- Cosign container signing
- Trivy container security
- Checkov IaC scanning
- Bandit SAST
- Kubernetes admission policies

### Observability & SRE

- Prometheus
- Grafana
- Loki
- Tempo
- OpenTelemetry
- Alertmanager
- Custom Prometheus exporters
- Dashboards-as-code
- Metrics, logs, and distributed traces
- Trace-to-log correlation

### Backend & Distributed Systems

- Python / FastAPI
- Node.js / TypeScript / Express
- Go
- PostgreSQL
- Redis
- RabbitMQ
- Kafka
- BullMQ
- WebSockets
- Distributed locking
- Idempotency
- Circuit breakers
- Retry and dead-letter queue patterns

---

# Featured Projects

## Infrastructure

### [infra-core](https://github.com/cypher682/infra-core)

Production-oriented AWS infrastructure platform provisioned with Terraform and configured with Ansible.

- Multi-AZ VPC architecture
- Application Load Balancer
- EC2 Auto Scaling Group
- RDS PostgreSQL
- Private application infrastructure
- Zero inbound SSH
- AWS SSM Session Manager for operational access
- CIS-aligned Linux hardening with Ansible
- GitHub Actions using short-lived AWS OIDC credentials
- Infrastructure security validation with Checkov
- Automated deployment smoke testing

`AWS` `Terraform` `Ansible` `SSM` `RDS` `ALB` `GitHub Actions`

---

## Cloud Security

### [cloudguard-pro](https://github.com/cypher682/cloudguard-pro)

Event-driven AWS security detection and remediation platform.

- CloudTrail → EventBridge → Lambda security event pipeline
- Seven Python Lambda functions for security automation
- Automated remediation of exposed security-group rules
- S3 public-access protection
- IAM security remediation
- Scheduled CIS-aligned AWS security scanning
- DynamoDB-based event and finding storage
- Terraform and Pulumi infrastructure implementations
- 70+ automated tests
- Bandit, Checkov, and Trivy integrated into CI

`Python` `AWS Lambda` `EventBridge` `DynamoDB` `Terraform` `Pulumi` `SNS`

---

## Cloud-Native Systems

### [nexuspay-platform](https://github.com/cypher682/nexuspay-platform)

Cloud-native fintech platform demonstrating microservices, financial integrity, asynchronous messaging, and Kubernetes-based delivery.

- Four decoupled services:
  - API Gateway
  - Authentication
  - Payments
  - Notifications
- Double-entry ledger using integer minor units
- Strict payment state transitions
- RabbitMQ asynchronous processing
- Dead-letter queue architecture
- HMAC-signed webhooks
- Redis-backed services
- Helm deployment architecture
- ArgoCD GitOps delivery
- ArgoCD ApplicationSets
- OPA/Gatekeeper policy enforcement
- k6 load testing
- OpenAPI contract validation
- Trivy container scanning

`TypeScript` `Express 5` `PostgreSQL` `Redis` `RabbitMQ` `Kubernetes` `Helm` `ArgoCD`

---

## GitOps & Progressive Delivery

### [gitops-pipeline](https://github.com/cypher682/gitops-pipeline)

GitOps delivery platform combining continuous delivery, progressive deployment, and software supply-chain security.

- GitLab CI application pipeline
- ArgoCD declarative deployment
- Argo Rollouts progressive canary delivery
- Prometheus-based deployment analysis
- Automated rollback on failed metrics
- Cosign cryptographic container signing
- SOPS + AGE encrypted secrets
- Kubernetes admission controls
- Helm-based deployment configuration

`GitLab CI` `ArgoCD` `Argo Rollouts` `Kubernetes` `Helm` `Cosign` `SOPS` `AGE`

---

## Observability

### [observability-platform](https://github.com/cypher682/observability-platform)

Vendor-neutral observability platform for metrics, logs, and distributed traces.

- Prometheus metrics collection
- Grafana visualization
- Loki centralized logging
- Tempo distributed tracing
- OpenTelemetry Collector
- TraceID-based log/trace correlation
- Custom Python Prometheus exporter
- Seven Grafana dashboards
- Dashboards provisioned as code
- Alertmanager severity-based routing
- Docker Compose and Kubernetes deployment support

`Prometheus` `Grafana` `Loki` `Tempo` `OpenTelemetry` `Alertmanager` `Python`

---

## Distributed Systems

### [nodeflow-api](https://github.com/cypher682/nodeflow-api)

Distributed background-job and webhook orchestration engine designed around reliability and high concurrency.

- BullMQ + Redis distributed job processing
- Prioritized jobs
- Delayed and scheduled execution
- Retry handling
- Dead-letter queues
- Exponential backoff with jitter
- HMAC-SHA256 webhook signing
- Circuit-breaker protection
- Real-time WebSocket job updates
- Distributed locking
- Idempotency controls
- PostgreSQL persistence

`Node.js` `TypeScript` `BullMQ` `Redis` `PostgreSQL` `WebSockets` `Prisma`

---

# Systems Foundations

## [ecs-production-platform](https://github.com/cypher682/ecs-production-platform)

Production AWS ECS Fargate platform demonstrating infrastructure automation and blue-green deployment.

- 36+ Terraform-managed AWS resources
- VPC networking
- Application Load Balancer
- ECS Fargate
- RDS PostgreSQL
- ACM SSL termination
- Route 53 DNS
- ALB weighted target groups
- Blue-green deployment strategy
- Tested rollback procedures
- OIDC-based CI/CD
- Infrastructure verification and teardown evidence

`Terraform` `AWS ECS Fargate` `ALB` `RDS` `Route 53` `ACM`

---

## [authcore-service](https://github.com/cypher682/authcore-service)

Security-focused IAM service implementing modern authentication and authorization patterns.

- OAuth2 Authorization Code flow with PKCE
- TOTP MFA
- Refresh-token family management
- Refresh-token reuse detection
- Dynamic RBAC
- Redis-backed rate limiting
- Progressive brute-force protection
- Authentication audit trails
- PostgreSQL persistence
- Celery background processing
- Alembic migrations
- Dockerized deployment

`FastAPI` `Python` `PostgreSQL` `Redis` `Celery` `OAuth2` `Docker`

---

## [vpcctl-linux-networking](https://github.com/cypher682/vpcctl-linux-networking)

Linux networking CLI demonstrating the underlying primitives behind cloud networking.

- Linux network namespaces
- Virtual Ethernet pairs
- Linux bridges
- IP routing
- iptables NAT
- Local virtual network construction
- Python CLI automation

`Python` `Linux` `Networking` `Namespaces` `veth` `iptables`

---

# Engineering Principles

\`\`\`text
Provision everything
        ↓
Infrastructure as Code

Deploy declaratively
        ↓
GitOps

Authenticate without long-lived credentials
        ↓
OIDC / Short-lived credentials

Operate without open SSH
        ↓
SSM / Controlled access

Secure the software supply chain
        ↓
Sign → Scan → Verify

Observe before debugging
        ↓
Metrics + Logs + Traces

Design for failure
        ↓
Retries + DLQs + Circuit Breakers

Protect data integrity
        ↓
Idempotency + Transactions + Exact Accounting

Automate repetitive operations
        ↓
CI/CD + Policy + Remediation
\`\`\`

## Technical Stack

| Domain | Technologies |
|---|---|
| Cloud Platforms | AWS, Azure |
| AWS Infrastructure | VPC, EC2, ASG, ALB, RDS, ECS Fargate, S3, IAM, SSM |
| AWS Security | GuardDuty, Security Hub, AWS Config, CloudTrail, KMS |
| IaC | Terraform, Pulumi, CloudFormation |
| Configuration | Ansible |
| Containers | Docker, Docker Compose |
| Orchestration | Kubernetes, Helm |
| Platform Engineering | ArgoCD, Argo Rollouts, OPA/Gatekeeper |
| CI/CD | GitHub Actions, GitLab CI, Jenkins |
| Supply Chain Security | Cosign, SOPS, AGE, Trivy |
| IaC Security | Checkov |
| SAST | Bandit |
| Observability | Prometheus, Grafana, Loki, Tempo, OpenTelemetry, Alertmanager |
| Backend | Python, FastAPI, Node.js, TypeScript, Express, Go |
| Databases | PostgreSQL, Redis |
| Messaging | RabbitMQ, Kafka, BullMQ |
| Systems | Linux, Bash, namespaces, veth, bridges, iptables |

---

# Certifications

- **Kubernetes and Cloud Native Associate (KCNA)**
  *Cloud Native Computing Foundation (CNCF)*

- **Linux Foundation Training**
  - LFS101 — Introduction to Linux
  - LFS158 — Introduction to Kubernetes

---

# GitHub Activity

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=cypher682&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="150" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=cypher682&layout=compact&theme=tokyonight&hide_border=true" height="150" />
</p>

<p align="center">
  <i>Build it. Automate it. Secure it. Observe it.</i>
</p>
