# ☁️ CloudNative: Professional Spring Cloud Microservices Blueprint

![CloudNative Hero Banner](/home/raven/.gemini/antigravity/brain/0e34cd78-0977-463f-ad0b-5adbc09a1bac/cloudnative_micro_hero_banner_1777060957591.png)

CloudNative is a production-ready demonstration of distributed systems using **Spring Boot 3** and **Spring Cloud**. It provides a complete blueprint for building, discovering, and monitoring microservices in a cloud-native environment, integrated with modern observability tools like **Grafana**, **Prometheus**, and **Micrometer**.

## 🏗️ Architectural Blueprint

The platform is designed with a decentralized approach, ensuring high availability and fault tolerance across all services.

```mermaid
graph TD
    User((User)) --> Gateway[API Gateway - Spring Cloud Gateway]
    Gateway --> Discovery[Discovery Server - Eureka]
    Gateway --> Config[Config Server - Spring Cloud Config]
    
    Gateway --> Customers[Customers Service]
    Gateway --> Vets[Vets Service]
    Gateway --> Visits[Visits Service]
    Gateway --> GenAI[GenAI Chatbot Service]
    
    Customers --> DB1[(HSQLDB/MySQL)]
    Vets --> DB2[(HSQLDB/MySQL)]
    Visits --> DB3[(HSQLDB/MySQL)]
    
    subgraph "Observability & Ops"
    Monitor[Grafana Dashboards]
    Metrics[Prometheus]
    Tracing[Zipkin Tracing]
    Admin[Spring Boot Admin]
    end
    
    Gateway -.-> Metrics
    Customers -.-> Metrics
    Vets -.-> Metrics
    Visits -.-> Metrics
```

## ⚡ Key Microservices

- **API Gateway**: Unified entry point with intelligent routing and circuit breaking.
- **Service Discovery**: Automated detection and load balancing via Netflix Eureka.
- **Centralized Config**: Externalized configuration management for all environments.
- **GenAI Service**: Advanced AI-powered chatbot for natural language interaction.
- **Observability Stack**: Full-spectrum monitoring with Micrometer and Prometheus.

## 🔄 AI Interaction Flow

```mermaid
sequenceDiagram
    participant U as User
    participant G as API Gateway
    participant AI as GenAI Service
    participant C as Customer Service
    participant L as LLM (OpenAI/Azure)

    U->>G: Ask: "Who owns a dog named Moopsie?"
    G->>AI: Route Request
    AI->>C: Fetch Customer Data
    C-->>AI: Return Customer List
    AI->>L: Process Query with Context
    L-->>AI: "Betty owns Moopsie."
    AI-->>G: JSON Response
    G-->>U: Render Chat Message
```

## 🚀 Getting Started

### 1. Build the Artifacts
```bash
./mvnw clean install
```

### 2. Launch with Docker Compose
```bash
docker compose up -d
```

### 3. Key Access Points
- **Frontend Portal**: `http://localhost:8080`
- **Discovery Dashboard**: `http://localhost:8761`
- **Grafana Metrics**: `http://localhost:3030`
- **Config Server**: `http://localhost:8888`

## 📦 Cloud Infrastructure

The stack is fully containerized and optimized for **Kubernetes** deployment. It includes health checks and graceful shutdown procedures to ensure zero-downtime updates.

---
*Architected and Refined by Saanvi Rajput. Pioneering Cloud-Native Excellence.*
