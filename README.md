# DAPR Workshop

Welcome to the DAPR (Distributed Application Runtime) Workshop! This hands-on workshop will guide you through the fundamentals of building distributed applications using DAPR.

## 🎯 Workshop Objectives

By the end of this workshop, you will:

- Understand DAPR's core concepts and building blocks
- Learn how to build microservices with DAPR
- Implement service-to-service communication
- Work with state management and pub/sub messaging
- Deploy DAPR applications to Kubernetes
- Apply best practices for distributed application development

## 📋 Prerequisites

Before starting this workshop, ensure you have:

### Required Tools

- [Docker Desktop](https://docs.docker.com/get-docker/) (latest version)
- [DAPR CLI](https://docs.dapr.io/getting-started/install-dapr-cli/) (v1.12+)
- [Kubernetes](https://kubernetes.io/docs/tasks/tools/) (kubectl)
- [.NET 8 SDK](https://dotnet.microsoft.com/download) or [Node.js 18+](https://nodejs.org/)
- [Git](https://git-scm.com/downloads)
- Code editor ([VS Code](https://code.visualstudio.com/) recommended)

### Knowledge Prerequisites

- Basic understanding of microservices architecture
- Familiarity with containerization concepts
- Basic knowledge of REST APIs
- Understanding of distributed systems challenges

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ams0/dapr-workshop.git
cd dapr-workshop
```

### 2. Initialize DAPR

```bash
dapr init
```

### 3. Verify Installation

```bash
dapr --version
docker ps
```

You should see DAPR runtime containers running.

## 📚 Workshop Modules

### Module 1: DAPR Fundamentals

- **Duration**: 45 minutes
- **Topics**:
  - What is DAPR?
  - DAPR building blocks overview
  - Architecture and components
- **Lab**: Setting up your first DAPR application

### Module 2: Service Invocation

- **Duration**: 60 minutes
- **Topics**:
  - Service-to-service communication
  - Service discovery
  - Load balancing and retries
- **Lab**: Building a multi-service application

### Module 3: State Management

- **Duration**: 60 minutes
- **Topics**:
  - State stores and consistency
  - CRUD operations with state API
  - State encryption and querying
- **Lab**: Implementing a stateful service

### Module 4: Pub/Sub Messaging

- **Duration**: 75 minutes
- **Topics**:
  - Event-driven architecture
  - Message brokers and topics
  - Dead letter queues and retries
- **Lab**: Building an event-driven system

### Module 5: Bindings and Secrets

- **Duration**: 45 minutes
- **Topics**:
  - Input/Output bindings
  - External system integration
  - Secret management
- **Lab**: Connecting to external services

### Module 6: Observability

- **Duration**: 45 minutes
- **Topics**:
  - Distributed tracing
  - Metrics and logging
  - Health checks
- **Lab**: Monitoring DAPR applications

### Module 7: Production Deployment

- **Duration**: 90 minutes
- **Topics**:
  - DAPR on Kubernetes
  - Configuration management
  - Security best practices
- **Lab**: Deploying to AKS/EKS

## 🏗️ Workshop Architecture

This workshop uses a sample e-commerce application with the following services:

```text
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Order Service │    │  Inventory Svc  │
│   (React/Vue)   │◄──►│   (.NET/Node)   │◄──►│   (.NET/Python) │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │                       ▼                       │
         │            ┌─────────────────┐                │
         └───────────►│  DAPR Runtime   │◄───────────────┘
                      └─────────────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
    ┌─────────▼────┐  ┌────────▼────┐  ┌───────▼──────┐
    │   Redis      │  │   RabbitMQ  │  │  PostgreSQL  │
    │  (State)     │  │  (Pub/Sub)  │  │  (External)  │
    └──────────────┘  └─────────────┘  └──────────────┘
```

## 📁 Repository Structure

```text
dapr-workshop/
├── src/
│   ├── frontend/           # React frontend application
│   ├── order-service/      # Order management service
│   ├── inventory-service/  # Inventory management service
│   └── notification-service/ # Email/SMS notifications
├── dapr/
│   ├── components/         # DAPR component configurations
│   └── configurations/     # DAPR configurations
├── k8s/
│   ├── manifests/         # Kubernetes deployment files
│   └── helm/              # Helm charts (optional)
├── scripts/
│   ├── setup.sh          # Environment setup script
│   └── deploy.sh         # Deployment script
└── docs/
    ├── troubleshooting.md
    └── resources.md
```

## 🛠️ Quick Start Commands

### Local Development

```bash
# Start all services locally
./scripts/setup.sh

# Run individual services with DAPR
dapr run --app-id order-service --app-port 3000 --dapr-http-port 3001 npm start
```

### Kubernetes Deployment

```bash
# Deploy DAPR to Kubernetes
dapr init -k

# Deploy workshop applications
kubectl apply -f k8s/manifests/
```

## 🔧 Troubleshooting

### Common Issues

#### DAPR CLI not found

```bash
# Verify installation
which dapr
dapr --version
```

#### Docker containers not starting

```bash
# Check Docker status
docker ps
docker logs dapr_placement
```

#### Port conflicts

```bash
# Check port usage
lsof -i :3000
# Kill conflicting processes if needed
```

### Getting Help

- Check the [troubleshooting guide](docs/troubleshooting.md)
- Review DAPR [official documentation](https://docs.dapr.io/)
- Ask questions in workshop discussions

## 📖 Additional Resources

### Documentation

- [DAPR Official Docs](https://docs.dapr.io/)
- [DAPR Concepts](https://docs.dapr.io/concepts/)
- [DAPR Best Practices](https://docs.dapr.io/operations/best-practices/)

### Community

- [DAPR GitHub](https://github.com/dapr/dapr)
- [DAPR Discord](https://discord.com/invite/ptHhX6jc34)
- [DAPR Blog](https://blog.dapr.io/)

### Videos and Tutorials

- [DAPR YouTube Channel](https://www.youtube.com/channel/UCtpSQ9BLB_3EXdWAUQYwnRA)
- [Microsoft Learn - DAPR](https://docs.microsoft.com/learn/paths/microservices-dapr/)

## 🤝 Contributing

We welcome contributions to improve this workshop! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

## 📄 License

This workshop is licensed under the [MIT License](LICENSE).

## 🙋‍♀️ Support

For questions or issues:

- Open an issue in this repository
- Contact the workshop facilitators
- Join our community discussions

---

**Happy Learning with DAPR!** 🚀

Last updated: July 2025