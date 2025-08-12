# Serverless Service Comparison – Azure vs AWS vs GCP

This document maps the Microsoft Azure serverless services used in our application to equivalent offerings in **Amazon Web Services (AWS)** and **Google Cloud Platform (GCP)**, and compares them in terms of **Integration Options** and **Monitoring & Observability**.

---

## Comparison Table

| Azure Service | AWS Equivalent | GCP Equivalent | Integration Options | Monitoring & Observability |
|---------------|---------------|----------------|----------------------|----------------------------|
| **Azure Functions** (Triggers & Bindings) | AWS Lambda | Cloud Functions | **Azure**: Native bindings to Storage, Event Hubs, Service Bus, Cosmos DB; integrates with Azure DevOps, GitHub Actions. **AWS**: Integrates with S3, DynamoDB, SNS/SQS, API Gateway, Step Functions, CodePipeline. **GCP**: Integrates with Pub/Sub, Cloud Storage, Firestore, Cloud Scheduler, Cloud Build. | **Azure**: Azure Monitor, Application Insights. **AWS**: CloudWatch Logs, X-Ray. **GCP**: Cloud Logging, Cloud Trace, Cloud Monitoring. |
| **Durable Functions** (Chaining, Orchestration, Fan-out/Fan-in) | AWS Step Functions | Workflows | **Azure**: Built-in orchestration with stateful functions; integrates with all Function bindings. **AWS**: Visual workflow orchestration with Lambda and services; integrates with SNS/SQS, API Gateway, DynamoDB. **GCP**: Orchestration with Workflows calling Cloud Functions, Cloud Run, APIs. | **Azure**: Application Insights traces for orchestration steps. **AWS**: Step Functions execution history in CloudWatch. **GCP**: Workflows logs in Cloud Logging. |
| **Azure Logic Apps** | AWS Step Functions (Express workflows) / EventBridge Scheduler | Workflows + Eventarc | **Azure**: 300+ connectors to SaaS and Azure services; integrates with CI/CD via Azure DevOps/GitHub Actions. **AWS**: Step Functions with API Gateway for integrations, EventBridge for triggers. **GCP**: Workflows with connectors, Eventarc for event triggers. | **Azure**: Logic Apps run history, Azure Monitor. **AWS**: CloudWatch Events/Logs. **GCP**: Cloud Logging for workflows. |
| **Azure Service Bus** (Queues & Topics) | Amazon SQS (queues) + SNS (topics) | Pub/Sub | **Azure**: Service Bus triggers for Functions; integrates with Logic Apps, Event Grid. **AWS**: SQS triggers for Lambda, SNS fan-out to multiple subscribers. **GCP**: Pub/Sub triggers for Cloud Functions and Dataflow. | **Azure**: Azure Monitor metrics, dead-letter queues. **AWS**: CloudWatch metrics and DLQs. **GCP**: Cloud Monitoring metrics, DLQs. |
| **Azure Event Grid** | Amazon EventBridge | Eventarc | **Azure**: Native event-driven model; integrates with Functions, Logic Apps, Service Bus. **AWS**: EventBridge for routing events to Lambda, Step Functions, SNS. **GCP**: Eventarc for routing events to Cloud Run, Workflows, Functions. | **Azure**: Event delivery logs in Azure Monitor. **AWS**: EventBridge logs in CloudWatch. **GCP**: Eventarc logs in Cloud Logging. |
| **Azure Event Hubs** | Amazon Kinesis Data Streams | Pub/Sub | **Azure**: Integrates with Stream Analytics, Functions, Databricks. **AWS**: Kinesis with Lambda, Firehose, analytics services. **GCP**: Pub/Sub with Dataflow, Functions, BigQuery. | **Azure**: Azure Monitor metrics, capture logs. **AWS**: CloudWatch metrics for shard usage, throughput. **GCP**: Cloud Monitoring metrics for Pub/Sub topics. |

---

## Notes

- The chosen AWS and GCP equivalents aim for functional parity, though some services differ in scope or architecture.
- Integration depth varies per platform — Azure Functions has a strong binding model, AWS Lambda relies on service-specific triggers, and GCP Functions relies on Pub/Sub and HTTP triggers.
- Monitoring tools differ in naming but offer similar capabilities: logs, metrics, and tracing.

---

## References

- [Azure Serverless Documentation](https://learn.microsoft.com/azure/azure-functions/)
- [AWS Serverless Documentation](https://docs.aws.amazon.com/serverless/)
- [GCP Serverless Documentation](https://cloud.google.com/serverless)

```

If you want, I can also **add a “Service Mapping” section above this** so that your GitHub README has an internal link like:

```md
- [Service Mapping](#serverless-service-comparison--azure-vs-aws-vs-gcp)
```

That way, your “Service Mapping” will jump directly to this table in the same document.
