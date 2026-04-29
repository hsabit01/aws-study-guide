# AGENTS.md

## Purpose

This repository contains AWS SAA study notes as individual Markdown files inside the `notes/` directory.

Your task is to generate or update `README.md` so it acts as a clear study index for the AWS services in this folder.

The README must group the existing service note files by learning order and close relationship. It should use tables, not long paragraphs.

## Main Task

Create a `README.md` that contains:

1. A short title and introduction.
2. A recommended learning order.
3. Grouped sections using the exact group order below.
4. A Markdown table under each group.
5. A filename correction section for typos or inconsistent AWS service names.
6. A short “How to Use This Study Guide” section.

## Directory and Link Requirement

All AWS service note files are stored inside the `notes/` directory.

Every service listed in the README must link to its corresponding file inside `notes/`.

Use links like this:

```md
[IAM](notes/IAM.md)
[API Gateway](notes/API%20Gateway.md)
[Route 53](notes/Route%2053.md)
[Elastic Load Balancing](notes/Elastic%20Load%20Balancer.md)
```

Do not generate root-level links like:

```md
[IAM](IAM.md)
[Route 53](Route%2053.md)
```

The `File` column in every README table must use `notes/` links.

Do not delete or rename any existing service `.md` files unless explicitly asked. The README should only reference the files inside the `notes/` directory.

## README Style Requirements

Use clean GitHub-flavored Markdown.
Each table row should include:

- `Order`: the study order within that group.
- `Service`: the corrected AWS service name.
- `File`: a relative Markdown link to the existing file inside `notes/`, for example `[IAM](notes/IAM.md)`.
- `Learn With`: closely related services from the same or nearby groups.
- `Why It Belongs Here`: one concise sentence explaining the relationship.

Keep explanations concise, beginner-friendly, and exam-focused.

## Required Groups and Files

Use the following group order and file placement.

### 01 - Core Foundations

All files are under the `notes/` directory.

| Order | Service | Existing File |
|---:|---|---|
| 1 | IAM | `IAM.md` |
| 2 | AWS Organizations | `Organizations.md` |
| 3 | Amazon VPC | `VPC.md` |

Learning focus:

- Identity and access first.
- Multi-account structure second.
- Networking foundation third.

### 02 - Networking, Routing, and Edge

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon Route 53 | `Route 53.md` |
| 2 | Elastic Load Balancing | `Elastic Load Balancer.md` |
| 3 | Amazon CloudFront | `CloudFront.md` |
| 4 | AWS Global Accelerator | `Global Accelerator.md` |
| 5 | Amazon API Gateway | `API Gateway.md` |
| 6 | AWS Certificate Manager | `ACM.md` |
| 7 | AWS WAF | `WAF.md` |
| 8 | AWS Network Firewall | `Network Firewall.md` |
| 9 | AWS Site-to-Site VPN | `Site-to-Site VPN.md` |
| 10 | AWS Direct Connect | `Direct Connect.md` |

Learning focus:

- DNS, traffic routing, load balancing, CDN, and edge protection.
- Hybrid connectivity with VPN and Direct Connect.
- Security at the edge with ACM, WAF, and Network Firewall.

### 03 - Compute and Application Hosting

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon EC2 | `EC2.md` |
| 2 | Amazon EBS | `EBS.md` |
| 3 | AWS Elastic Beanstalk | `Elastic Beanstalk.md` |
| 4 | Amazon ECS | `ECS.md` |
| 5 | Amazon EKS | `EKS.md` |
| 6 | AWS Lambda | `Lambda.md` |
| 7 | Serverless Architecture | `Serverless.md` |

Learning focus:

- Start with EC2 because many AWS compute concepts build on it.
- Learn EBS with EC2 because it is EC2 block storage.
- Then learn managed app platforms, containers, Kubernetes, and serverless.

### 04 - Storage and Data Transfer

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon S3 | `S3.md` |
| 2 | Amazon EFS | `EFS.md` |
| 3 | Amazon FSx | `FSx.md` |
| 4 | AWS Storage Gateway | `Storage Gateway.md` |
| 5 | AWS DataSync | `DataSync.md` |
| 6 | AWS Snowball | `Snowball.md` |

Learning focus:

- Object, file, and hybrid storage.
- Data movement and migration patterns.
- SAA exam comparisons: S3 vs EFS vs FSx vs Storage Gateway vs DataSync vs Snowball.

### 05 - Databases and Caching

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon RDS | `RDS.md` |
| 2 | Amazon Aurora | `Aurora.md` |
| 3 | Amazon DynamoDB | `DynamoDB.md` |
| 4 | Amazon ElastiCache | `ElastiCash.md` |
| 5 | AWS Database Migration Service | `DMS.md` |

Learning focus:

- Relational databases first.
- Aurora as AWS-optimized relational database.
- DynamoDB as NoSQL.
- ElastiCache for caching.
- DMS for database migration.

### 06 - Messaging, Streaming, and Event-Driven Architecture

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon SQS | `SQS.md` |
| 2 | Amazon SNS | `SNS.md` |
| 3 | Amazon EventBridge | `EventBridge.md` |
| 4 | Amazon Kinesis Data Streams | `Kensis Data Stream.md` |
| 5 | Amazon Kinesis Data Firehose | `Kensis Data Firehose.md` |

Learning focus:

- Queueing, pub/sub, event buses, and streaming.
- SAA exam comparisons: SQS vs SNS vs EventBridge vs Kinesis.

### 07 - Security, Encryption, and Identity

| Order | Service | Existing File |
|---:|---|---|
| 1 | AWS KMS | `KMS.md` |
| 2 | AWS Secrets Manager | `Secret Management Service.md` |
| 3 | AWS Directory Service | `Directory Service.md` |
| 4 | Amazon GuardDuty | `GuardDuty.md` |
| 5 | AWS CloudTrail | `CloudTrail.md` |
| 6 | AWS Config | `Config.md` |

Learning focus:

- Encryption and secrets.
- Directory integration.
- Threat detection, auditing, and compliance tracking.

Note: IAM is intentionally placed in Core Foundations, but it should also be referenced here as a related service.

### 08 - Monitoring, Management, and Operations

| Order | Service | Existing File |
|---:|---|---|
| 1 | Amazon CloudWatch | `CloudWatch.md` |
| 2 | AWS Systems Manager | `System Manager.md` |
| 3 | AWS Backup | `Backup.md` |
| 4 | Disaster Recovery | `Disaster Recovery.md` |

Learning focus:

- Observability, operational management, backup, and resilience.
- SAA exam scenarios around alarms, logs, patching, automation, RTO, and RPO.

### 09 - Analytics, Data Lake, and Machine Learning

| Order | Service | Existing File |
|---:|---|---|
| 1 | AWS Glue | `Glue.md` |
| 2 | AWS Lake Formation | `Lake Formation.md` |
| 3 | Amazon EMR | `EMR.md` |
| 4 | Amazon SageMaker | `SageMaker.md` |

Learning focus:

- ETL, data lakes, big data processing, and ML.
- Keep explanations SAA-level, not machine-learning-engineer-level.

### 10 - Hybrid Cloud and Migration

| Order | Service | Existing File |
|---:|---|---|
| 1 | AWS Outposts | `Outposts.md` |
| 2 | AWS Storage Gateway | `Storage Gateway.md` |
| 3 | AWS Snowball | `Snowball.md` |
| 4 | AWS DataSync | `DataSync.md` |
| 5 | AWS Database Migration Service | `DMS.md` |
| 6 | AWS Direct Connect | `Direct Connect.md` |
| 7 | AWS Site-to-Site VPN | `Site-to-Site VPN.md` |

Learning focus:

- Hybrid workloads and migration patterns.
- Some services appear in earlier groups and should be cross-referenced here instead of duplicated as separate notes.

## Recommended Learning Order Section

The README must include this ordered list:

```md
1. IAM + Organizations + VPC
2. EC2 + EBS + ELB + Route 53
3. S3 + EFS + FSx
4. RDS + Aurora + DynamoDB + ElastiCache
5. CloudFront + WAF + ACM + Global Accelerator
6. SQS + SNS + EventBridge
7. Lambda + API Gateway + Serverless
8. CloudWatch + CloudTrail + Config + Systems Manager
9. KMS + Secrets Manager + GuardDuty + Directory Service
10. Backup + Disaster Recovery
11. DataSync + Storage Gateway + Snowball + DMS
12. ECS + EKS + Elastic Beanstalk
13. Glue + Lake Formation + EMR + SageMaker
14. Direct Connect + Site-to-Site VPN + Outposts
```

## Filename Correction Section

Add a section called:

```md
## Recommended Filename Corrections
```

Include this table:

| Current Filename | Recommended Filename | Reason |
|---|---|---|
| `ElastiCash.md` | `ElastiCache.md` | Correct AWS service spelling. |
| `Kensis Data Stream.md` | `Kinesis Data Streams.md` | Correct AWS service name and plural form. |
| `Kensis Data Firehose.md` | `Kinesis Data Firehose.md` | Correct AWS service spelling. |
| `Secret Management Service.md` | `Secrets Manager.md` | Correct AWS service name. |
| `System Manager.md` | `Systems Manager.md` | Correct AWS service name. |

Important:

- Do not rename files automatically.
- README links must point to the current existing filenames unless the files have already been renamed.
- If you decide to rename files in a separate task, update README links after renaming.

## Link Rules

When writing README links:

- Use relative Markdown links.
- Preserve spaces in filenames unless the repository style requires URL encoding.
- Example: `[Route 53](notes/Route%2053.md)` is acceptable if spaces break links in the environment.
- Prefer links that work in GitHub preview.
- Every README subject link must point to the matching file under `notes/`.
- Example format: `[IAM](notes/IAM.md)`.
- For filenames with spaces, use URL-encoded spaces if needed, for example `[API Gateway](notes/API%20Gateway.md)`.
- Do not link to files from the repository root, because the service files are not stored there.

## Quality Checklist

Before finishing, verify:

- Every file from the source list appears at least once.
- Every service link points to the corresponding file inside `notes/`.
- Every group has a table.
- The README is beginner-friendly and AWS SAA-focused.
- Tables are readable in GitHub.
- Typos in service names are corrected in display names.
- Existing filenames are not silently changed.
- Duplicate cross-group services are clearly explained as cross-references.
- No unrelated AWS services are added.
- No long essays are added.

## Tone

Use a simple, concise, exam-focused tone.

The reader is learning AWS Solutions Architect Associate topics and wants to understand which services should be studied together.
