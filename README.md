# Edwin Bulter - Portfolio

Cloud-native software engineer specializing in microservices architecture, Kubernetes, and secure distributed systems.

[LinkedIn Profile](https://www.linkedin.com/in/edwin-bulter-68b29015/) | [GitHub Profile](https://github.com/edwinbulter)

---

## Recent Selfstudy Projects (December 2025 - Present)

The following projects (Demo 1-11) represent my ongoing selfstudy and exploration of modern cloud-native technologies, security patterns, and distributed systems architecture.

---

## Projects

### 1. Nordic Wonen – Serverless Event-Driven Webshop (AWS)

Architectural & QA automation proof of concept: serverless, event-driven webshop architecture on AWS with clean Python code, Infrastructure-as-Code, and a two-tier automated test strategy.

A portfolio project styled as an IKEA-like lamp shop (not affiliated with IKEA; product images are hotlinked from ikea.com and product names are fictional). Focuses on event-driven decoupling, a single-table DynamoDB design, thorough OWASP Top 10 coverage, and a GDPR/NIS2 compliance analysis.

**Key Features:**
- Single Flask Lambda (via Mangum/ASGI) serving server-rendered HTML with HTMX, behind API Gateway with a custom domain (Route53 + ACM)
- DynamoDB single-table design with a GSI for price-sorted catalog queries
- Event-driven order processing: EventBridge custom bus fans out an `OrderPlaced` event to three SQS queues (payment, inventory, notification), each with its own DLQ for fault isolation
- Comprehensive OWASP Top 10 (2025) security measures, documented per category
- [GDPR (AVG) and NIS2 (Cyberbeveiligingswet) compliance analysis](https://github.com/edwinbulter/webshop-aws-python/blob/main/docs/gdpr-nis2-compliance.md): personal data inventory, legal basis per processing activity, data subject rights implemented in the app (access, rectification, account deletion, JSON data export), retention periods, processors and EU-only data residency, plus a NIS2 applicability assessment - with remaining gaps (privacy statement, data breach protocol, automated retention cleanup) documented explicitly
- Infrastructure-as-Code with Terraform (modules per component, including custom domain and GitHub OIDC)
- Two-tier automated testing: pytest/moto integration tests and Playwright E2E tests
- CI/CD with GitHub Actions using OIDC authentication (no long-lived AWS credentials stored - uses temporary tokens for deployment)
- Dependency and Python version management with uv

**Stack:** Python, Flask, HTMX, Jinja2, Mangum, AWS Lambda, API Gateway, DynamoDB, EventBridge, SQS, Route53, ACM, Terraform, GitHub Actions, pytest/moto, Playwright, uv

**Repository:** [github.com/edwinbulter/webshop-aws-python](https://github.com/edwinbulter/webshop-aws-python)

---

### 2. BankSim – Zero-Trust Internet Banking Simulation (Kubernetes)

Internet banking simulation for 10 fictional households with about five years of realistic transaction history. An admin can move the simulation date; all account holders then see their accounts as if it were that day.

Built as a zero-trust, security-first reference architecture running in its own namespace in a local kind cluster, with functional and technical design documents (in Dutch) covering architecture, API, data model, security, OWASP Top 10:2025, resilience, testing and deployment.

**Key Features:**
- Customer screens: account overview, payment account with paged transactions and advanced search, payments to known contacts with a confirmation step (no overdraft), and a savings account with 3% interest calculated daily and credited monthly
- Admin screens: overview of all account holders, read-only transaction inspection and setting the simulation date
- Backend-for-Frontend (Spring Cloud Gateway) handling OIDC login with Keycloak, keeping tokens server-side behind an encrypted HttpOnly cookie session, with rate limiting
- Zero trust: JWT validation in the API, mTLS between all components with a dedicated BankSim CA, and default-deny NetworkPolicies
- Atomic transfers through a single ledger service, with `BigDecimal`/`NUMERIC(19,2)` amounts end to end
- OWASP Top 10:2025 measures documented per category (A01–A10)
- Resilience: starts without database or Keycloak, timeouts, circuit breakers and idempotent payments
- Deterministic fake data generator for 10 households (October 2021 – December 2026)
- Backend tests: unit, integration (Testcontainers), architecture, contract and mutation tests; Playwright E2E suite covering all scenarios in Chromium, Firefox and WebKit
- Supply chain and CI: GitHub Actions running OpenAPI contract checks, OWASP Dependency-Check, SBOMs, Trivy image scans and the E2E suite in an ephemeral kind cluster; images and Actions pinned by digest, kept up to date by Renovate

**Stack:** Java 21, Spring Boot, Spring Cloud Gateway, Keycloak, PostgreSQL, Flyway, Angular, TypeScript, Playwright, Helm, Kubernetes (kind), ingress-nginx, GitHub Actions, Trivy

**Repository:** [github.com/edwinbulter/banksim](https://github.com/edwinbulter/banksim)

---

### 3. MBD – Cloud-Native Microservices

Scalable platform focused on defense-in-depth via Service Mesh and event-driven architecture.

A fictional investment-banking application designed as a security testing sandbox and DevSecOps learning platform. The project demonstrates modern cloud-native security patterns and includes intentional vulnerabilities for testing security scanning tools.

**Key Features:**
- Service mesh (Istio) for encrypted service-to-service communication (mTLS)
- GitOps deployment via ArgoCD
- PKI certificate management with cert-manager
- Single sign-on through Keycloak with JWT validation
- Event-driven architecture with Apache Kafka
- User registration, investment accounts, fund trading, and portfolio monitoring

**Stack:** Kotlin, Spring Boot 3.1, React 18, TypeScript, Istio, Kafka, Keycloak, ArgoCD, PostgreSQL, Kubernetes (kind)

**Repository:** [github.com/edwinbulter/mbd](https://github.com/edwinbulter/mbd)

---

### 4. K8s Security – Zero-Trust Kubernetes Architecture

Seven independent Proof of Concepts demonstrating a layered security architecture for Kubernetes environments based on zero-trust principles: "Never trust, always verify."

**Security Layers:**
1. User Identity & SSO – Authentication via Keycloak and OAuth2-Proxy
2. Workload Identity & Service Mesh – Machine-to-machine encryption using Istio and mutual TLS
3. PKI-Driven Service Mesh – Organization-wide trust chains through certificate management
4. Federated Identity – Live integration with external PostgreSQL user databases
5. User Permissions – Custom JWT claims injection from external data sources
6. Identity Governance – midPoint + Keycloak integration for lifecycle management
7. Passwordless Authentication – WebAuthn/passkey implementation in Keycloak

**Stack:** Java, Kubernetes, Istio, Keycloak, cert-manager, midPoint

**Repository:** [github.com/edwinbulter/k8-security](https://github.com/edwinbulter/k8-security)

---

### 5. Multi-Cloud Quote App (AWS, Azure, OVH)

Secure multi-cloud app with JWT/OAuth authentication across cloud providers.

Full-stack serverless application for managing inspirational quotes, demonstrating cloud-native development practices across multiple cloud providers. Users can browse quotes from the ZenQuotes API, bookmark favorites, and view popular quotes ranked by engagement.

**Key Features:**
- Email/password and Google OAuth authentication
- Lambda optimization with SnapStart
- Infrastructure-as-Code with Terraform
- CI/CD with GitHub Actions using OIDC authentication (no long-lived AWS credentials stored - uses temporary tokens for deployment)
- Multi-cloud deployment guides for AWS, Azure, and OVHcloud
- Multi-language backends: Java, C# and Go
- Live demo environments for production and development

**Stack:** React 18, TypeScript, Vite, TailwindCSS, Java 21 Lambda, API Gateway, DynamoDB, S3, CloudFront, Terraform, GitHub Actions

**Repository:** [github.com/edwinbulter/quote-lambda-tf](https://github.com/edwinbulter/quote-lambda-tf)

---

### 6. Azure Kubernetes Service (AKS) Deployment

Architecture, setup and configuration of AKS cluster including JWT and identity management.

Experimental learning project demonstrating .NET application deployment to Azure Kubernetes Service. The repository showcases the complete journey from local development through production-ready cloud deployment.

**Learning Stages:**
1. Migration from Azure Function App to Container Web App
2. Local Kubernetes deployment using Docker Desktop
3. AKS deployment with automated infrastructure
4. Terraform deployment to Azure Container Apps (planned)

**Focus Areas:**
- Docker containerization of .NET 8.0 applications
- Infrastructure automation through Azure CLI scripts
- Cost-optimized testing using spot instances
- Zero-cost resource cleanup strategies
- Security best practices for containerized workloads

**Stack:** C#, .NET 8.0, React, Kubernetes (AKS), Docker, Azure CLI, Terraform

**Repository:** [github.com/edwinbulter/quote-azure-k8](https://github.com/edwinbulter/quote-azure-k8)

---

### 7. Hybrid Kubernetes Engine (Scaleway & Kind)

Integration of cloud (Scaleway) and local (Kind) Kubernetes clusters.

Cloud-agnostic Kubernetes implementation of a quote application, refactored from an Azure-specific project to reduce vendor lock-in and enable multi-cloud deployment.

**Key Objectives:**
- Cloud Independence: Remove Azure-specific dependencies
- Local Development: Enable local testing using Kind (Kubernetes in Docker)
- Cost-Effective Hosting: Demonstrate deployment to Scaleway with minimized infrastructure expenses
- Technology Migration: Port backend from C# to Java using Quarkus for improved performance

**Project Structure:**
- `k8-quote-api/` – Quarkus-based Java backend
- `k8-quote-frontend/` – React frontend application
- `k8/` – Kubernetes configuration files
- `scripts/` – Deployment utilities

**Stack:** Java, Quarkus, React, Kubernetes, Kind, JWT authentication

**Repository:** [github.com/edwinbulter/quote-k8-java](https://github.com/edwinbulter/quote-k8-java)

---

### 8. Mobile App Development

Native iOS/Android apps with focus on clean code and UX.

Multi-platform educational application for practicing multiplication and division tables, available as React web app, native Android application, and native iOS application.

**Features:**
- Table Selection: 18 predefined tables including decimal values (0.125 to 25)
- Dual Operations: Practice both multiplication and division
- Custom Tables: Input any number for specialized practice
- Interactive Sessions: Ten questions per practice round with immediate feedback
- Virtual Keyboard: Touch-friendly numeric input optimized for mobile screens
- Scoreboard: Track and manage personal best times with sorting capabilities
- User Profiles: Progress tracking by username with local data persistence

**Web Stack:** React 19, Vite, Tailwind CSS, React Router, PostCSS, AWS (S3, CloudFront), Terraform

**Android Stack:** Kotlin, Android Jetpack, Room Database, Material Design

**iOS Stack:** Swift, SwiftUI

**Live Demo:** Available on CloudFront (web) and Google Play Store (Android)

**Repository:** [github.com/edwinbulter/multiplication-trainer](https://github.com/edwinbulter/multiplication-trainer)

---

### 9. Spring Integration Demos

Practical implementation of Enterprise Integration Patterns (EIP) using Spring Integration in Kubernetes environments. Demonstrates message-driven architecture through a four-application pipeline that processes quotes: fetching data, file polling, Kafka streaming with JSON transformation, and dual consumption patterns (file writing and PostgreSQL persistence).

**Key Concepts:**
- File processing with directory polling and content transformation
- Event-driven systems using Kafka with declarative message routing
- System connectivity via pre-built adapters (databases, files, messaging)
- Message orchestration with splitting, aggregation, and error handling

**Stack:** Java, Spring Integration, Spring Boot, Kafka, PostgreSQL, Kubernetes (kind), Maven

**Repository:** [github.com/edwinbulter/spring-integration](https://github.com/edwinbulter/spring-integration)

---

### 10. Quote K8s Python – Flask/HTMX Monolith

A Python/Flask + HTMX port of the [quote-k8-java](https://github.com/edwinbulter/quote-k8-java) project, running in a local kind Kubernetes cluster.

Unlike the Java original (a separate Quarkus API + React SPA + MongoDB), this version is a single Flask monolith: server-rendered HTML (Jinja2) with HTMX for interactivity, backed by SQLite on a PVC. One container, one pod, one Deployment.

**Key Features:**
- Quote-browsing app with per-user favourites and viewed-quote history
- Admin screens for user and quote management
- Server-rendered HTML with HTMX for interactivity (no separate frontend build)
- SQLite persistence on a PersistentVolumeClaim

**Stack:** Python, Flask, HTMX, Jinja2, SQLite, Kubernetes (kind)

**Repository:** [github.com/edwinbulter/quote-k8s-python](https://github.com/edwinbulter/quote-k8s-python)

---

### 11. Quote AWS Lambda Python – Serverless Flask/HTMX

A port of the [quote-k8s-python](https://github.com/edwinbulter/quote-k8s-python) Flask/HTMX app from Kubernetes to a single AWS Lambda function, following the pattern of the [quote-lambda-tf](https://github.com/edwinbulter/quote-lambda-tf) Java backend but with one Lambda, one Terraform folder, and one AWS environment.

Same app, same HTML/HTMX UI, same routes - the database and auth layers are what changed: a Lambda cannot host a local SQLite file, and concurrent Lambda instances need stateless, independently verifiable authentication.

**Key Features:**
- Single Flask Lambda behind API Gateway, serving server-rendered HTML with HTMX
- DynamoDB persistence, including a quote-id counter and transactional like-count consistency
- AWS Cognito authentication with JWT verification in the Lambda
- Infrastructure-as-Code with Terraform (DynamoDB, Cognito, Lambda, API Gateway, IAM, CloudWatch)
- Offline pytest suite using moto-mocked DynamoDB and Cognito
- Opt-in Playwright browser e2e test suite (`tests_e2e/`) covering auth, quote browsing (anonymous and authenticated), favourites, viewed-quote history, profile, role-based UI, and admin screens
- Design docs covering architecture, auth flow, DynamoDB schema, deployment, expected AWS costs, and e2e testing setup/running/debugging

**Stack:** Python, Flask, HTMX, Jinja2, AWS Lambda, API Gateway, DynamoDB, Cognito, Terraform, pytest/moto, Playwright, uv

**Live Demo:** Personal deployment on API Gateway (no uptime guarantee)

**Repository:** [github.com/edwinbulter/quote-aws-lambda-python](https://github.com/edwinbulter/quote-aws-lambda-python)

---

## Previous Experience (2024)

### AWS Serverless Event-Driven App

This project was created in 2024 to build first step experience with AWS as an API backend for different frontends. It demonstrates the design and implementation of a scalable, serverless backend architecture with fine-grained authorization (Fine-Grained Access Control).

**Purpose:** Experimental project to gain hands-on experience with AWS serverless services while exploring how a single backend API can serve multiple frontend frameworks.

**Architecture:**
- Python-based AWS Lambda functions
- AWS Cognito for user management and authentication
- Custom Lambda Authorizer with AWS Verified Permissions (Cedar policy engine)
- Fine-Grained Access Control for API security
- Central authorization logic

**Supported Frontends:**
1. **React web application** – Modern React implementation hosted on AWS Amplify
2. **Flutter web application** – Cross-platform Flutter implementation
3. **Angular web application** – Angular-based frontend
4. **JavaFX desktop application** – Desktop GUI with custom authentication dialogs

**Backend Stack:** Python, AWS Lambda, AWS Cognito, AWS Verified Permissions, Cedar

**Frontend Stack:** React, Flutter, Angular, JavaFX

**Repositories:**
- Backend: [github.com/edwinbulter/klik_backend](https://github.com/edwinbulter/klik_backend)
- React Frontend: [github.com/edwinbulter/klik_react](https://github.com/edwinbulter/klik_react)
- Flutter Frontend: [github.com/edwinbulter/klik_flutter](https://github.com/edwinbulter/klik_flutter)
- Angular Frontend: [github.com/edwinbulter/klik_angular](https://github.com/edwinbulter/klik_angular)
- JavaFX Frontend: [github.com/edwinbulter/klik_javafx](https://github.com/edwinbulter/klik_javafx)

---

## Contact

For more information about these projects or collaboration opportunities, please connect via [LinkedIn](https://www.linkedin.com/in/edwin-bulter-68b29015/).
