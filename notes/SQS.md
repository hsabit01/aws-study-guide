# Amazon SQS

## 1. Definition

<details>
<summary><strong>Simple definition</strong></summary>

Amazon SQS, or **Simple Queue Service**, is a fully managed **message queue** service.

It lets one part of an application send messages to a queue, and another part process those messages later.

**Memory hook:**  
**SQS = “Store Queue Safely”**

</details>

<details>
<summary><strong>Beginner example</strong></summary>

Imagine a restaurant:

- Customers place orders.
- Orders go into a queue.
- Kitchen staff pick up orders one by one.
- If the kitchen is busy, orders wait safely in the queue.

In AWS:

- Producer = sends message
- SQS queue = stores message
- Consumer = processes message

</details>

---

## 2. What Problem Does It Solve?

<details>
<summary><strong>Decouples applications</strong></summary>

SQS helps separate application components so they do not depend on each other being available at the same time.

Example:

- A web app receives an order.
- Instead of processing payment, email, inventory, and shipping immediately, it sends a message to SQS.
- Worker services process those tasks later.

This improves reliability and scalability.

</details>

<details>
<summary><strong>Handles traffic spikes</strong></summary>

If 10,000 requests arrive suddenly, SQS can hold messages while workers process them at their own speed.

Without SQS, backend services could be overloaded.

</details>

<details>
<summary><strong>Prevents data loss during failures</strong></summary>

If a worker crashes while processing a task, the message can become visible again and another worker can retry it.

</details>

---

## 3. Core Use Cases

<details>
<summary><strong>Background job processing</strong></summary>

Use SQS when users should not wait for slow work.

Examples:

- Image resizing
- Video processing
- Sending emails
- Generating reports
- Processing payments asynchronously

</details>

<details>
<summary><strong>Decoupling microservices</strong></summary>

Service A can send messages to SQS without directly calling Service B.

This reduces tight coupling between services.

</details>

<details>
<summary><strong>Buffering traffic spikes</strong></summary>

SQS can absorb sudden request bursts and allow consumers to process messages gradually.

</details>

<details>
<summary><strong>Retry and failure handling</strong></summary>

Failed messages can be retried automatically.

Messages that keep failing can be moved to a **dead-letter queue**, or DLQ.

</details>

<details>
<summary><strong>Fanout with SNS</strong></summary>

SNS can publish one message to multiple SQS queues.

This is useful when multiple systems need to process the same event differently.

Example:

- One queue for email service
- One queue for analytics service
- One queue for billing service

</details>

---

## 4. Important Features for SAA

<details>
<summary><strong>Queue types: Standard vs FIFO</strong></summary>

| Queue Type | Ordering | Duplicate Handling | Throughput | Best For |
|---|---:|---:|---:|---|
| Standard Queue | Best-effort ordering | At-least-once delivery, duplicates possible | Very high | Most workloads |
| FIFO Queue | Strict order within message group | Exactly-once processing behavior using deduplication | Lower than standard, but supports high-throughput FIFO mode | Ordered processing |

**Exam memory hook:**

- **Standard = speed**
- **FIFO = order**

</details>

<details>
<summary><strong>Standard queues</strong></summary>

Standard queues are the default SQS queue type.

Key exam points:

- Very high throughput
- At-least-once delivery
- Duplicate messages are possible
- Ordering is best-effort, not guaranteed
- Consumers must be idempotent

**Idempotent** means processing the same message twice does not cause incorrect results.

</details>

<details>
<summary><strong>FIFO queues</strong></summary>

FIFO means **First-In, First-Out**.

Key exam points:

- Preserves message order within a **message group**
- Helps prevent duplicate processing
- Requires `.fifo` queue name suffix
- Requires `MessageGroupId`
- Uses deduplication with:
  - `MessageDeduplicationId`, or
  - Content-based deduplication

**Important:** FIFO ordering is guaranteed only within the same message group.

</details>

<details>
<summary><strong>Message visibility timeout</strong></summary>

Visibility timeout is the time a message is hidden after a consumer receives it.

Flow:

1. Consumer receives message.
2. SQS hides the message.
3. Consumer processes the message.
4. Consumer deletes the message.
5. If not deleted before timeout, message becomes visible again.

Default visibility timeout: **30 seconds**  
Maximum visibility timeout: **12 hours**

**Exam trap:**  
Visibility timeout does not delete the message.

</details>

<details>
<summary><strong>Message retention</strong></summary>

Message retention controls how long SQS keeps messages that are not deleted.

Default retention: **4 days**  
Maximum retention: **14 days**  
Minimum retention: **1 minute**

**Exam hook:**  
SQS is not long-term storage. Use S3 for long-term storage.

</details>

<details>
<summary><strong>Dead-letter queue, or DLQ</strong></summary>

A DLQ stores messages that fail processing multiple times.

You configure:

- Source queue
- DLQ target
- Maximum receive count

If a message fails too many times, SQS moves it to the DLQ.

Use DLQs for:

- Debugging failures
- Isolating bad messages
- Preventing poison messages from blocking processing

**Exam trap:**  
A FIFO queue must use a FIFO DLQ.  
A standard queue must use a standard DLQ.

</details>

<details>
<summary><strong>Long polling</strong></summary>

Long polling waits for messages to arrive before returning a response.

Benefits:

- Reduces empty responses
- Reduces cost
- Improves efficiency

Maximum long polling wait time: **20 seconds**

**Exam hook:**  
Use long polling to reduce cost and unnecessary API calls.

</details>

<details>
<summary><strong>Short polling</strong></summary>

Short polling returns immediately, even if no messages are available.

It can create more empty responses and higher cost.

For most exam scenarios, long polling is preferred.

</details>

<details>
<summary><strong>Delay queues</strong></summary>

A delay queue postpones delivery of new messages.

Maximum delay: **15 minutes**

Use when messages should not be processed immediately.

Example:

- Wait 5 minutes before checking payment status.

</details>

<details>
<summary><strong>Message timers</strong></summary>

Message timers delay individual messages.

They are similar to delay queues, but apply per message.

Important distinction:

| Feature | Scope |
|---|---|
| Delay queue | Entire queue |
| Message timer | Individual message |

</details>

<details>
<summary><strong>Maximum message size</strong></summary>

SQS messages can be up to **1 MiB**.

For larger payloads, store the large object in S3 and send an S3 pointer through SQS.

**Exam hook:**  
SQS message = pointer or instruction, not large file storage.

</details>

<details>
<summary><strong>Batch actions</strong></summary>

SQS supports batching up to **10 messages** per API call.

Common batch actions:

- SendMessageBatch
- DeleteMessageBatch
- ChangeMessageVisibilityBatch

Batching helps reduce cost and improve throughput.

</details>

<details>
<summary><strong>Lambda integration</strong></summary>

AWS Lambda can poll SQS and process messages automatically.

Important points:

- Lambda polls the queue.
- Lambda invokes the function with message batches.
- Failed messages can be retried.
- DLQs can capture repeated failures.

**Exam trap:**  
SQS itself is pull-based. Consumers poll SQS.

</details>

---

## 5. Security Model

<details>
<summary><strong>IAM permissions</strong></summary>

Access to SQS is controlled with IAM policies.

Common permissions:

| Action | Purpose |
|---|---|
| `sqs:SendMessage` | Allows sending messages |
| `sqs:ReceiveMessage` | Allows reading messages |
| `sqs:DeleteMessage` | Allows deleting processed messages |
| `sqs:ChangeMessageVisibility` | Allows extending or changing visibility timeout |
| `sqs:GetQueueAttributes` | Allows reading queue settings |

Use least privilege.

Example:

- Producer only needs `SendMessage`.
- Consumer usually needs `ReceiveMessage`, `DeleteMessage`, and `ChangeMessageVisibility`.

</details>

<details>
<summary><strong>Queue policies</strong></summary>

SQS supports resource-based queue policies.

Queue policies are useful when allowing another AWS account or service to access a queue.

Example:

- Allow SNS topic to send messages to SQS.
- Allow another AWS account to send messages.

</details>

<details>
<summary><strong>Encryption at rest</strong></summary>

SQS supports server-side encryption.

Options:

| Encryption Option | Description |
|---|---|
| SQS-managed encryption | AWS manages encryption for you |
| AWS KMS key | Use AWS-managed or customer-managed KMS keys |

Use KMS when you need more control over key access and auditing.

</details>

<details>
<summary><strong>Encryption in transit</strong></summary>

Messages should be sent over HTTPS using TLS.

This protects messages while moving between clients and SQS.

</details>

<details>
<summary><strong>KMS permissions</strong></summary>

If using SSE with KMS, producers and consumers may need KMS permissions.

Common KMS permissions:

- `kms:GenerateDataKey`
- `kms:Decrypt`

**Exam trap:**  
Having SQS permissions alone may not be enough if the queue uses a customer-managed KMS key.

</details>

<details>
<summary><strong>Network/security controls</strong></summary>

SQS is a regional public AWS service endpoint, but you can access it privately using an **interface VPC endpoint**, powered by AWS PrivateLink.

Benefits:

- Private access from VPC
- No internet gateway required
- Better security control with endpoint policies

</details>

<details>
<summary><strong>Shared responsibility</strong></summary>

| AWS Responsibility | Customer Responsibility |
|---|---|
| Manages SQS infrastructure | Configure IAM correctly |
| Provides durability and availability | Enable encryption if required |
| Handles scaling | Delete messages after processing |
| Secures underlying service | Use DLQs and retries properly |
| Maintains service operations | Avoid sending sensitive data unless protected |

</details>

---

## 6. High Availability / Durability Behavior

<details>
<summary><strong>Availability</strong></summary>

SQS is a highly available managed service.

You do not manage servers, clusters, or brokers.

AWS handles the infrastructure.

</details>

<details>
<summary><strong>Fault tolerance</strong></summary>

SQS stores messages redundantly across multiple servers.

If a consumer fails, the message can become visible again after the visibility timeout.

This allows another consumer to retry processing.

</details>

<details>
<summary><strong>Multi-AZ behavior</strong></summary>

SQS is designed to be highly available within an AWS Region.

Messages are stored redundantly across multiple Availability Zones in the Region.

**Exam hook:**  
You do not configure Multi-AZ for SQS. AWS handles it.

</details>

<details>
<summary><strong>Multi-Region behavior</strong></summary>

SQS queues are regional.

A queue exists in one AWS Region.

For Multi-Region architectures, you must design replication or failover yourself.

Example options:

- Use applications to publish messages to queues in multiple Regions.
- Use EventBridge for cross-Region event routing where appropriate.
- Use disaster recovery patterns with active-active or active-passive design.

</details>

<details>
<summary><strong>Durability</strong></summary>

SQS is durable for messages during the configured retention period.

Messages remain in the queue until:

- A consumer deletes them after successful processing.
- The retention period expires.
- They are moved to a DLQ after repeated failures.

</details>

---

## 7. Cost Optimization Options

<details>
<summary><strong>Use long polling</strong></summary>

Long polling reduces empty responses.

Fewer empty receives means fewer unnecessary API requests.

This is one of the most common SQS cost optimization exam answers.

</details>

<details>
<summary><strong>Use batch operations</strong></summary>

Send, receive, and delete messages in batches when possible.

Batching up to 10 messages per request can reduce API call volume.

</details>

<details>
<summary><strong>Choose the right queue type</strong></summary>

Use standard queues unless strict ordering or deduplication is required.

FIFO queues are useful, but do not choose FIFO unless the workload needs ordering.

</details>

<details>
<summary><strong>Delete messages after processing</strong></summary>

Consumers must delete messages after successful processing.

If messages are not deleted, they can be retried repeatedly and increase processing cost.

</details>

<details>
<summary><strong>Use appropriate retention</strong></summary>

Do not keep messages longer than needed.

Longer retention can be useful for recovery, but SQS is not meant for long-term data storage.

</details>

<details>
<summary><strong>Use S3 for large payloads</strong></summary>

For large data, store the payload in S3 and send only a pointer in SQS.

This keeps queue messages small and avoids inefficient message handling.

</details>

<details>
<summary><strong>Scale consumers carefully</strong></summary>

Too few consumers can create backlog.

Too many consumers can increase compute cost.

Use Auto Scaling, Lambda concurrency, or ECS scaling based on queue depth.

</details>

---

## 8. Common Exam Traps

<details>
<summary><strong>Trap: SQS pushes messages to consumers</strong></summary>

Wrong.

SQS is normally **poll-based**.

Consumers poll the queue to receive messages.

Lambda integration feels automatic, but Lambda is polling SQS behind the scenes.

</details>

<details>
<summary><strong>Trap: Standard queues guarantee ordering</strong></summary>

Wrong.

Standard queues provide best-effort ordering only.

Use FIFO queues when strict ordering is required.

</details>

<details>
<summary><strong>Trap: Standard queues deliver exactly once</strong></summary>

Wrong.

Standard queues provide at-least-once delivery.

Duplicate messages are possible.

Design consumers to be idempotent.

</details>

<details>
<summary><strong>Trap: Visibility timeout deletes a message</strong></summary>

Wrong.

Visibility timeout only hides the message temporarily.

The consumer must delete the message after successful processing.

</details>

<details>
<summary><strong>Trap: DLQ automatically fixes failed messages</strong></summary>

Wrong.

A DLQ isolates failed messages.

You still need to inspect, fix, and optionally redrive them.

</details>

<details>
<summary><strong>Trap: FIFO means the entire queue is single-threaded</strong></summary>

Not exactly.

FIFO preserves order within each message group.

Multiple message groups can be processed in parallel.

</details>

<details>
<summary><strong>Trap: SQS is good for real-time pub/sub fanout by itself</strong></summary>

Not by itself.

SQS is a queue.

For fanout, use SNS publishing to multiple SQS queues.

</details>

<details>
<summary><strong>Trap: SQS is the same as Kinesis</strong></summary>

Wrong.

SQS is for decoupled message processing.

Kinesis is for streaming data with ordered shards and replay capability.

</details>

<details>
<summary><strong>Trap: SQS stores messages forever</strong></summary>

Wrong.

Maximum retention is 14 days.

For long-term storage, use S3.

</details>

<details>
<summary><strong>Trap: Any DLQ type can be attached to any queue</strong></summary>

Wrong.

Queue types must match:

- Standard queue → standard DLQ
- FIFO queue → FIFO DLQ

</details>

---

## 9. Compare With Similar Services

<details>
<summary><strong>SQS vs similar AWS messaging services</strong></summary>

| Service | Pattern | Choose When | Key Exam Point |
|---|---|---|---|
| SQS | Queue | You need decoupling and async processing | Pull-based queue |
| SNS | Pub/sub | You need to fan out one message to many subscribers | Push-based notifications |
| EventBridge | Event bus | You need event routing, SaaS integration, or rule-based filtering | Best for event-driven apps |
| Kinesis Data Streams | Streaming | You need ordered streaming, replay, and analytics | Uses shards |
| Amazon MQ | Managed message broker | You need protocols like AMQP, MQTT, OpenWire, JMS | Best for legacy broker migration |
| Step Functions | Workflow orchestration | You need multi-step workflows with state and retries | Coordinates services |
| Lambda Async Invocation | Async compute trigger | You want Lambda to handle async retry flow directly | Not a general queue replacement |

</details>

<details>
<summary><strong>When to choose SQS</strong></summary>

Choose SQS when:

- You need a buffer between services.
- You want asynchronous processing.
- You need retries.
- You need DLQ support.
- You want workers to process jobs at their own pace.
- You do not need complex event routing.

</details>

<details>
<summary><strong>When not to choose SQS</strong></summary>

Do not choose SQS when:

- You need one event delivered to many systems directly → use SNS or EventBridge.
- You need long-term message replay beyond 14 days → use Kinesis or S3-based design.
- You need streaming analytics → use Kinesis.
- You need complex workflows → use Step Functions.
- You need traditional broker protocols → use Amazon MQ.

</details>

---

## 10. Mini Architecture Example

<details>
<summary><strong>Architecture: Order processing with SQS</strong></summary>

Scenario:

An e-commerce app receives orders.

Instead of processing everything during the user request, the app sends order messages to SQS.

Workers process orders asynchronously.

Flow:

1. User places order through API Gateway.
2. Order service stores order in DynamoDB.
3. Order service sends message to SQS.
4. Lambda workers poll SQS.
5. Lambda processes payment, inventory, and email tasks.
6. Failed messages go to a DLQ.
7. CloudWatch monitors queue depth and failures.

</details>

<details>
<summary><strong>Mermaid diagram</strong></summary>

```mermaid
flowchart LR
    User["<b>User</b><br/>Places order"] --> APIGW["<b>API Gateway</b><br/>Receives request"]
    APIGW --> OrderSvc["<b>Order Service</b><br/>Validates order"]
    OrderSvc --> DB["<b>DynamoDB</b><br/>Stores order"]
    OrderSvc --> Queue["<b>Amazon SQS Queue</b><br/>Buffers order task"]
    Queue --> Lambda["<b>Lambda Workers</b><br/>Process messages"]
    Lambda --> Payment["<b>Payment Service</b>"]
    Lambda --> Email["<b>Email Service</b>"]
    Lambda --> Inventory["<b>Inventory Service</b>"]
    Queue --> DLQ["<b>Dead-Letter Queue</b><br/>Failed messages"]
    Queue --> CW["<b>CloudWatch</b><br/>Metrics and alarms"]

    style User fill:#3B82F6,stroke:#1E3A8A,color:#ffffff
    style APIGW fill:#22C55E,stroke:#166534,color:#ffffff
    style OrderSvc fill:#F97316,stroke:#9A3412,color:#ffffff
    style DB fill:#8B5CF6,stroke:#5B21B6,color:#ffffff
    style Queue fill:#06B6D4,stroke:#155E75,color:#ffffff
    style Lambda fill:#A855F7,stroke:#6B21A8,color:#ffffff
    style Payment fill:#10B981,stroke:#065F46,color:#ffffff
    style Email fill:#F59E0B,stroke:#92400E,color:#ffffff
    style Inventory fill:#EC4899,stroke:#9D174D,color:#ffffff
    style DLQ fill:#EF4444,stroke:#991B1B,color:#ffffff
    style CW fill:#6366F1,stroke:#3730A3,color:#ffffff
```

</details>

<details>
<summary><strong>Why SQS fits this design</strong></summary>

SQS is useful here because:

- The user gets a fast response.
- Workers can process orders independently.
- Traffic spikes are buffered.
- Failed messages can be retried.
- Bad messages can be moved to a DLQ.
- The system becomes more fault tolerant.

</details>

---

## SAA Quick Review

<details>
<summary><strong>Must-remember facts</strong></summary>

| Topic | Exam Fact |
|---|---|
| Standard queue | High throughput, at-least-once delivery, best-effort ordering |
| FIFO queue | Ordered processing within message group, deduplication support |
| Visibility timeout | Message is hidden after being received |
| Delete message | Required after successful processing |
| DLQ | Stores repeatedly failed messages |
| Long polling | Reduces empty responses and cost |
| Retention | Default 4 days, maximum 14 days |
| Delay queue | Delays new messages up to 15 minutes |
| Message size | Up to 1 MiB |
| Large payloads | Store in S3 and send pointer in SQS |
| Security | IAM, queue policies, encryption, KMS, VPC endpoints |
| Multi-AZ | Handled by AWS within the Region |
| Multi-Region | Must be designed separately |

</details>

<details>
<summary><strong>Final memory hook</strong></summary>

**SQS = Queue for async work**

Remember:

- **Standard = speed**
- **FIFO = order**
- **Visibility timeout = hidden, not deleted**
- **DLQ = failed message parking lot**
- **Long polling = fewer empty calls**
- **SQS stores messages temporarily, not forever**

</details>