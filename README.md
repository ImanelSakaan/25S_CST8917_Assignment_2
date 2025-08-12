# CST8917 – Serverless Applications

# Multi-Cloud Serverless Services Comparison

## Overview

This repository provides a comprehensive comparison of serverless computing services across Microsoft Azure, Amazon Web Services (AWS), and Google Cloud Platform (GCP). The analysis focuses on equivalent services, features, pricing, and integration capabilities to help teams make informed decisions when migrating or adopting multi-cloud serverless architectures.

<img width="1024" height="1024" alt="Multi-Cloud Serverless Services Comparison" src="https://github.com/user-attachments/assets/ec9898d4-09ae-48ce-88ac-3523c8250915" />


## Table of Contents

- [Service Mapping](#service-mapping)
- [Core Features](#core-features)
- [Integration and Monitoring](#integration-and-monitoring)
- [Pricing Comparison](#pricing-comparison)
- [Strengths and Weaknesses](#strengths-and-weaknesses)
- 
- [Detailed Comparisons](#detailed-comparisons)
  - [Function as a Service (FaaS)](#function-as-a-service-faas)
  - [Workflow Orchestration](#workflow-orchestration)
  - [Event Processing](#event-processing)
  - [Messaging Services](#messaging-services)
- [Feature Matrix](#feature-matrix)

- [Migration Considerations](#migration-considerations)
- [Recommendations](#recommendations)

---

## Service Mapping

| Azure Service | AWS Equivalent | GCP Equivalent | Primary Use Case |
|---------------|----------------|----------------|------------------|
| Azure Functions | AWS Lambda | Google Cloud Functions | Function as a Service (FaaS) |
| Durable Functions | AWS Step Functions | Google Cloud Workflows | Workflow orchestration and state management |
| Azure Logic Apps | AWS Step Functions + SQS/SNS | Google Cloud Workflows + Pub/Sub | Visual workflow orchestration |
| Azure Service Bus | Amazon SQS/SNS | Google Cloud Pub/Sub | Message queuing and pub/sub |
| Azure Event Grid | Amazon EventBridge | Google Cloud Eventarc | Event routing and filtering |
| Azure Event Hubs | Amazon Kinesis Data Streams | Google Cloud Pub/Sub (streaming) | Real-time data streaming |

---
## Core Features
Comparison of serverless function services between Azure, AWS, and GCP.

| Feature | Azure Functions | AWS Lambda | Google Cloud Functions |
| --- | --- | --- | --- |
| Trigger Types | HTTP, Timer, Blob, Queue, Event Grid, Service Bus, Cosmos DB | S3, DynamoDB, Kinesis, API Gateway, EventBridge | HTTP, Cloud Pub/Sub, Cloud Storage, Firestore, Eventarc |
| Bindings | Input & Output bindings for easy integration | No bindings, manual integration needed | Minimal bindings, event-based integration |
| Orchestration | Durable Functions | Step Functions | Workflows |
| Languages | C#, JavaScript, Python, Java, PowerShell, Go, etc. | Node.js, Python, Java, C#, Go, Ruby, custom runtimes | Node.js, Python, Go, Java, .NET |
| Monitoring | Azure Monitor, Application Insights | CloudWatch, X-Ray | Cloud Logging, Cloud Trace, Cloud Monitoring |

---

## Integration and Monitoring

| Azure Service | AWS Equivalent | GCP Equivalent | Integration Options | Monitoring & Observability |
|---------------|---------------|----------------|----------------------|----------------------------|
| **Azure Functions** (Triggers & Bindings) | AWS Lambda | Cloud Functions | **Azure**: Native bindings to Storage, Event Hubs, Service Bus, Cosmos DB; integrates with Azure DevOps, GitHub Actions. **AWS**: Integrates with S3, DynamoDB, SNS/SQS, API Gateway, Step Functions, CodePipeline. **GCP**: Integrates with Pub/Sub, Cloud Storage, Firestore, Cloud Scheduler, Cloud Build. | **Azure**: Azure Monitor, Application Insights. **AWS**: CloudWatch Logs, X-Ray. **GCP**: Cloud Logging, Cloud Trace, Cloud Monitoring. |
| **Durable Functions** (Chaining, Orchestration, Fan-out/Fan-in) | AWS Step Functions | Workflows | **Azure**: Built-in orchestration with stateful functions; integrates with all Function bindings. **AWS**: Visual workflow orchestration with Lambda and services; integrates with SNS/SQS, API Gateway, DynamoDB. **GCP**: Orchestration with Workflows calling Cloud Functions, Cloud Run, APIs. | **Azure**: Application Insights traces for orchestration steps. **AWS**: Step Functions execution history in CloudWatch. **GCP**: Workflows logs in Cloud Logging. |
| **Azure Logic Apps** | AWS Step Functions (Express workflows) / EventBridge Scheduler | Workflows + Eventarc | **Azure**: 300+ connectors to SaaS and Azure services; integrates with CI/CD via Azure DevOps/GitHub Actions. **AWS**: Step Functions with API Gateway for integrations, EventBridge for triggers. **GCP**: Workflows with connectors, Eventarc for event triggers. | **Azure**: Logic Apps run history, Azure Monitor. **AWS**: CloudWatch Events/Logs. **GCP**: Cloud Logging for workflows. |
| **Azure Service Bus** (Queues & Topics) | Amazon SQS (queues) + SNS (topics) | Pub/Sub | **Azure**: Service Bus triggers for Functions; integrates with Logic Apps, Event Grid. **AWS**: SQS triggers for Lambda, SNS fan-out to multiple subscribers. **GCP**: Pub/Sub triggers for Cloud Functions and Dataflow. | **Azure**: Azure Monitor metrics, dead-letter queues. **AWS**: CloudWatch metrics and DLQs. **GCP**: Cloud Monitoring metrics, DLQs. |
| **Azure Event Grid** | Amazon EventBridge | Eventarc | **Azure**: Native event-driven model; integrates with Functions, Logic Apps, Service Bus. **AWS**: EventBridge for routing events to Lambda, Step Functions, SNS. **GCP**: Eventarc for routing events to Cloud Run, Workflows, Functions. | **Azure**: Event delivery logs in Azure Monitor. **AWS**: EventBridge logs in CloudWatch. **GCP**: Eventarc logs in Cloud Logging. |
| **Azure Event Hubs** | Amazon Kinesis Data Streams | Pub/Sub | **Azure**: Integrates with Stream Analytics, Functions, Databricks. **AWS**: Kinesis with Lambda, Firehose, analytics services. **GCP**: Pub/Sub with Dataflow, Functions, BigQuery. | **Azure**: Azure Monitor metrics, capture logs. **AWS**: CloudWatch metrics for shard usage, throughput. **GCP**: Cloud Monitoring metrics for Pub/Sub topics. |

---
## Pricing Comparison

### Function Execution Costs (as of 2024)

| Provider | Per Million Requests | Per GB-Second | Free Tier |
|----------|---------------------|---------------|-----------|
| **Azure Functions** | $0.20 | $0.000016 | 1M requests + 400K GB-s |
| **AWS Lambda** | $0.20 | $0.0000166667 | 1M requests + 400K GB-s |
| **Google Cloud Functions** | $0.40 | $0.0000025 (1st gen) / $0.0000024 (2nd gen) | 2M invocations + 400K GB-s |

### Workflow Orchestration Costs

| Provider | Pricing Model | Cost Structure |
|----------|---------------|----------------|
| **Durable Functions** | Function execution + storage | Same as Azure Functions + $0.05/GB storage |
| **AWS Step Functions** | Per state transition | Standard: $25 per million transitions<br>Express: $1 per million requests |
| **Cloud Workflows** | Per step execution | $0.01 per 1,000 internal steps |

### Event Processing Costs

| Provider | Service | Pricing |
|----------|---------|---------|
| **Azure** | Event Grid | $0.60 per million events |
| **AWS** | EventBridge | $1.00 per million events |
| **Google** | Eventarc | No additional cost (pay for compute) |

---
## Strengths and Weaknesses

| Cloud Provider | Strengths | Weaknesses |
| --- | --- | --- |
| **Azure** | - Tight integration with Microsoft ecosystem <br> - Rich developer tooling <br> - Durable Functions built-in orchestration <br> - Extensive triggers/bindings | - Smaller global footprint <br> - Steeper learning curve for non-MS devs <br> - Pricing complexity for orchestration |
| **AWS** | - Largest global footprint <br> - Wide event-source integration <br> - Mature monitoring & observability | - Vendor lock-in risk <br> - Cold start latency <br> - Orchestration requires Step Functions |
| **GCP** | - Strong data & AI/ML integration <br> - Simple deployment <br> - Competitive pricing | - Fewer regions <br> - Less mature event routing <br> - Historically fewer triggers |


---

## Detailed Comparisons

### Function as a Service (FaaS)

#### Azure Functions vs AWS Lambda vs Google Cloud Functions

**Azure Functions**
- **Triggers & Bindings**: 20+ built-in triggers (HTTP, Timer, Blob, Queue, etc.)
- **Language Support**: C#, JavaScript, Python, Java, PowerShell, TypeScript
- **Hosting Plans**: Consumption, Premium, Dedicated (App Service Plan)
- **Cold Start**: ~1-3 seconds (varies by plan)
- **Max Execution Time**: 5 minutes (Consumption), 30 minutes (Premium/Dedicated)
- **Scaling**: Automatic with Event-driven scale controller
- **Integration**: Native Azure ecosystem integration

**AWS Lambda**
- **Triggers**: 20+ event sources (API Gateway, S3, DynamoDB, etc.)
- **Language Support**: Python, JavaScript, Java, C#, Go, Ruby, PowerShell
- **Runtime Models**: On-demand, Provisioned Concurrency, Lambda@Edge
- **Cold Start**: ~100ms-1s (varies by language and memory)
- **Max Execution Time**: 15 minutes
- **Scaling**: Automatic up to 10,000 concurrent executions (configurable)
- **Integration**: Extensive AWS service integration

**Google Cloud Functions**
- **Triggers**: HTTP, Cloud Storage, Pub/Sub, Firebase, etc.
- **Language Support**: Python, JavaScript, Go, Java, .NET, Ruby, PHP
- **Generations**: 1st gen (legacy), 2nd gen (Cloud Run-based)
- **Cold Start**: ~1-3 seconds (1st gen), ~500ms (2nd gen)
- **Max Execution Time**: 9 minutes (1st gen), 60 minutes (2nd gen)
- **Scaling**: Automatic with configurable concurrency limits
- **Integration**: Google Cloud ecosystem integration

### Workflow Orchestration

#### Durable Functions vs Step Functions vs Cloud Workflows

**Azure Durable Functions**
- **Patterns**: Function chaining, fan-out/fan-in, async HTTP APIs, monitoring, human interaction
- **State Management**: Automatic state persistence and checkpointing
- **Programming Model**: Code-based orchestration (C#, JavaScript, Python)
- **Pricing**: Pay-per-execution + storage costs
- **Monitoring**: Application Insights integration
- **Scalability**: Inherits from Azure Functions scaling

**AWS Step Functions**
- **Workflow Types**: Standard (long-running), Express (high-volume, short-duration)
- **State Types**: Task, Choice, Parallel, Map, Pass, Wait, Succeed, Fail
- **Definition Language**: Amazon States Language (ASL) JSON-based
- **Pricing**: Pay-per-state-transition model
- **Monitoring**: CloudWatch and X-Ray integration
- **Visual Design**: Workflow Studio for visual editing

**Google Cloud Workflows**
- **Definition**: YAML-based workflow definition
- **Connectors**: 100+ pre-built connectors to Google Cloud services
- **Error Handling**: Built-in retry policies and error handling
- **Pricing**: Pay-per-step execution
- **Monitoring**: Cloud Logging and Cloud Monitoring integration
- **Security**: IAM-based access control

#### Azure Logic Apps vs AWS EventBridge + Step Functions

**Azure Logic Apps**
- **Connectors**: 400+ built-in connectors (SaaS, on-premises, Azure services)
- **Design**: Visual designer with drag-and-drop interface
- **Triggers**: 50+ trigger types (HTTP, schedule, event-based)
- **Pricing**: Pay-per-action execution
- **Integration**: Hybrid connectivity with on-premises data gateway
- **Templates**: Pre-built templates for common scenarios

**AWS EventBridge + Step Functions**
- **EventBridge**: Event bus service with 90+ SaaS integrations
- **Event Patterns**: JSON-based event filtering and routing
- **Custom Events**: Support for custom applications and SaaS providers
- **Archive/Replay**: Event replay capabilities
- **Cross-Region**: Global event replication support

### Event Processing

#### Azure Event Grid vs Amazon EventBridge vs Google Cloud Eventarc

**Azure Event Grid**
- **Event Sources**: 30+ Azure services + custom sources
- **Event Filtering**: Advanced filtering with boolean operators
- **Delivery Guarantees**: At-least-once delivery with dead-lettering
- **Pricing**: Pay-per-event ($0.60 per million events)
- **Schema Registry**: CloudEvents schema support
- **Security**: Managed identity and key-based authentication

**Amazon EventBridge**
- **Event Sources**: 90+ AWS services + SaaS providers
- **Custom Buses**: Multiple event buses per account
- **Schema Discovery**: Automatic schema discovery and registry
- **Pricing**: Pay-per-event ($1.00 per million events)
- **Archive**: Long-term event storage and replay
- **Global Replication**: Cross-region event replication

**Google Cloud Eventarc**
- **Event Sources**: Google Cloud services + custom sources
- **Cloud Events**: Native CloudEvents standard support
- **Destinations**: Cloud Run, Cloud Functions, GKE, Workflows
- **Pricing**: No additional cost (pay for underlying compute)
- **Audit Events**: Integration with Cloud Audit Logs
- **Multi-Region**: Global event routing capabilities

### Messaging Services

#### Azure Service Bus vs Amazon SQS/SNS vs Google Cloud Pub/Sub

**Azure Service Bus**
- **Queue Types**: Basic queues and topics/subscriptions
- **Message Features**: Sessions, duplicate detection, dead-lettering
- **Max Message Size**: 1MB (Premium: 100MB)
- **Pricing**: Pay-per-operation + throughput units
- **FIFO**: Guaranteed message ordering with sessions
- **Integration**: Native .NET SDK and REST API

**Amazon SQS/SNS**
- **SQS Types**: Standard (best-effort ordering) and FIFO queues
- **SNS**: Fan-out messaging to multiple subscribers
- **Max Message Size**: 256KB (SQS), 256KB (SNS)
- **Pricing**: Pay-per-request model
- **Delivery**: At-least-once delivery guarantee
- **Integration**: Extensive AWS service integration

**Google Cloud Pub/Sub**
- **Message Ordering**: Optional message ordering with keys
- **Delivery Types**: Pull and push subscription models
- **Max Message Size**: 10MB
- **Pricing**: Pay-per-message + throughput
- **Global**: Multi-region message replication
- **Integration**: Native Google Cloud service integration

#### Azure Event Hubs vs Amazon Kinesis vs Google Cloud Pub/Sub (Streaming)

**Azure Event Hubs**
- **Throughput Units**: Configurable ingress/egress capacity
- **Partitions**: Up to 1024 partitions per event hub
- **Retention**: 1-7 days (Standard), 90 days (Dedicated)
- **Pricing**: Pay-per-throughput unit + ingress events
- **Capture**: Automatic data capture to storage
- **Kafka**: Apache Kafka protocol support

**Amazon Kinesis Data Streams**
- **Shards**: Base throughput unit (1MB/sec ingress, 2MB/sec egress)
- **Retention**: 24 hours to 365 days
- **Scaling**: Manual or automatic shard scaling
- **Pricing**: Pay-per-shard-hour + data volume
- **Integration**: Native AWS analytics service integration
- **Enhanced Fan-out**: Dedicated throughput per consumer

**Google Cloud Pub/Sub (Streaming Mode)**
- **Throughput**: Automatic scaling without manual configuration
- **Retention**: Up to 7 days message retention
- **Ordering**: Per-key message ordering support
- **Pricing**: Pay-per-message model
- **Seek**: Message replay by timestamp
- **BigQuery**: Direct integration for analytics

---


## Feature Matrix

### Core Function Features

| Feature | Azure Functions | AWS Lambda | Google Cloud Functions |
|---------|----------------|------------|----------------------|
| **Languages** | C#, JS, Python, Java, PS | Python, JS, Java, C#, Go, Ruby | Python, JS, Go, Java, .NET |
| **Max Memory** | 1.5GB (Consumption) / 14GB (Premium) | 10GB | 8GB (2nd gen) |
| **Max Timeout** | 5min (Consumption) / 30min (Premium) | 15 minutes | 60 minutes (2nd gen) |
| **Cold Start** | 1-3 seconds | 100ms-1s | 500ms-3s |
| **Concurrency** | 200 (Consumption) / 500+ (Premium) | 10,000 (configurable) | 1,000 (2nd gen) |
| **VPC Support** | Virtual Network Integration | VPC configurations | VPC connector (2nd gen) |
| **Local Development** | Azure Functions Core Tools | SAM CLI / Serverless | Functions Framework |

### Orchestration Features

| Feature | Durable Functions | AWS Step Functions | Cloud Workflows |
|---------|------------------|-------------------|-----------------|
| **Definition** | Code-based (C#, JS, Python) | JSON (ASL) | YAML |
| **Visual Editor** | Limited (VS Code extension) | Workflow Studio | Limited |
| **Max Duration** | Unlimited (with checkpointing) | 1 year | 1 year |
| **State Management** | Automatic | JSON state passing | Variable-based |
| **Error Handling** | Try-catch in code | Built-in retry/catch states | Built-in retry policies |
| **Human Interaction** | Built-in approval patterns | Manual approval integration | External task patterns |

---



## Migration Considerations

### From Azure to AWS

**Functions to Lambda**
- Refactor binding attributes to event sources
- Update dependency injection patterns
- Modify logging from ILogger to CloudWatch
- Convert ARM templates to CloudFormation/SAM

**Durable Functions to Step Functions**
- Convert C#/JS orchestrators to ASL JSON
- Redesign state management approach
- Implement error handling in state definitions
- Migrate checkpointing logic to state machines

### From Azure to GCP

**Functions to Cloud Functions**
- Update trigger configurations
- Migrate to Cloud Functions Framework
- Convert to YAML deployment descriptors
- Update monitoring from App Insights to Cloud Monitoring

**Event Grid to Eventarc**
- Convert event schemas to CloudEvents format
- Update filtering logic
- Migrate webhook endpoints
- Reconfigure event routing rules

### Cross-Platform Patterns

**Multi-Cloud Event Architecture**
```yaml
# Example: Cross-cloud event processing
Azure Event Grid → HTTP Webhook → AWS Lambda → SQS → GCP Cloud Functions
```

**Hybrid Orchestration**
- Use REST APIs as integration points
- Implement compensating transaction patterns
- Design idempotent operations
- Maintain event sourcing for audit trails

---

## Recommendations

### When to Choose Azure
- **Enterprise Integration**: Strong Office 365 and on-premises integration needs
- **Hybrid Scenarios**: Existing Windows/.NET infrastructure
- **Logic Apps**: Need for visual workflow design with extensive connectors
- **Cost Efficiency**: Consistent pricing model across services

### When to Choose AWS
- **Ecosystem Maturity**: Most comprehensive serverless ecosystem
- **Advanced Patterns**: Complex event-driven architectures
- **Global Scale**: Multi-region deployments with edge computing
- **Analytics Integration**: Strong integration with AWS analytics services

### When to Choose GCP
- **Data Analytics**: Integration with BigQuery and ML services
- **Container-First**: Cloud Run-based functions (2nd gen)
- **Simplicity**: Cleaner pricing model for events
- **Open Standards**: Strong CloudEvents and Knative support

### Multi-Cloud Strategy
- **Event-Driven Integration**: Use CloudEvents standard across platforms
- **API Gateway Pattern**: Abstract provider-specific implementations
- **Monitoring**: Implement centralized observability (e.g., Datadog, New Relic)
- **IaC Tools**: Use Terraform for consistent infrastructure deployment

---

## Best Practices

### Security
- Enable managed identities/IAM roles instead of connection strings
- Implement least-privilege access principles
- Use secrets management services (Key Vault, Secrets Manager, Secret Manager)
- Enable audit logging and monitoring

### Performance
- Optimize memory allocation vs cost trade-offs
- Implement connection pooling and caching strategies
- Use provisioned concurrency for predictable workloads
- Monitor and optimize cold start performance

### Reliability
- Implement circuit breaker patterns
- Design for idempotency
- Use dead letter queues for failed messages
- Implement proper retry policies with exponential backoff

### Cost Optimization
- Right-size memory allocation based on profiling
- Use consumption-based pricing for variable workloads
- Implement function lifecycle management
- Monitor and alert on cost anomalies

---


*Last updated: August 2025*
























-------------------------------------------------------------------------------------------
