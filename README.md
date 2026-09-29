# Edwin Bulter - Portfolio

Cloud-native software engineer specializing in microservices architecture, Kubernetes, and secure distributed systems.

[LinkedIn Profile](https://www.linkedin.com/in/edwin-bulter-68b29015/) | [GitHub Profile](https://github.com/edwinbulter)

---

## Recent Selfstudy Projects (December 2025 - Present)

The following projects (Demo 1-9) represent my ongoing selfstudy and exploration of modern cloud-native technologies, security patterns, and distributed systems architecture.

---

## Projects

### 1. MBD (My Bank Demo) – Cloud-Native Microservices

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

### 2. K8 Security – Zero-Trust Kubernetes Architecture

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

### 3. Multi-Cloud Quote App (AWS, Azure, OVH)

Secure multi-cloud app with JWT/OAuth authentication across cloud providers.

Full-stack serverless application for managing inspirational quotes, demonstrating cloud-native development practices across multiple cloud providers. Users can browse quotes from the ZenQuotes API, bookmark favorites, and view popular quotes ranked by engagement.

**Key Features:**
- Email/password and Google OAuth authentication
- Lambda optimization with SnapStart
- Infrastructure-as-Code with Terraform
- CI/CD with GitHub Actions using OIDC authentication (no long-lived AWS credentials stored - uses temporary tokens for deployment)
- Multi-cloud deployment guides for AWS, Azure, and OVHcloud
- Live demo environments for production and development

**Stack:** React 18, TypeScript, Vite, TailwindCSS, Java 21 Lambda, API Gateway, DynamoDB, S3, CloudFront, Terraform, GitHub Actions

**Repository:** [github.com/edwinbulter/quote-lambda-tf](https://github.com/edwinbulter/quote-lambda-tf)

---

### 4. Azure Kubernetes Service (AKS) Deployment

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

### 5. Hybrid Kubernetes Engine (Scaleway & Kind)

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

### 6. Mobile App Development

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

### 7. Spring Integration Demos

Practical implementation of Enterprise Integration Patterns (EIP) using Spring Integration in Kubernetes environments. Demonstrates message-driven architecture through a four-application pipeline that processes quotes: fetching data, file polling, Kafka streaming with JSON transformation, and dual consumption patterns (file writing and PostgreSQL persistence).

**Key Concepts:**
- File processing with directory polling and content transformation
- Event-driven systems using Kafka with declarative message routing
- System connectivity via pre-built adapters (databases, files, messaging)
- Message orchestration with splitting, aggregation, and error handling

**Stack:** Java, Spring Integration, Spring Boot, Kafka, PostgreSQL, Kubernetes (kind), Maven

**Repository:** [github.com/edwinbulter/spring-integration](https://github.com/edwinbulter/spring-integration)

---

### 8. Quote K8s Python – Flask/HTMX Monolith

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

### 9. Quote AWS Lambda Python – Serverless Flask/HTMX

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

For more information about these projects or collaboration opportunities, please connect via [LinkedIn](https://www.linkedin.com/in/edwin-bulter-68b29015/) or visit my [GitHub profile](https://github.com/edwinbulter).
