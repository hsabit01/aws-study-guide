# AWS SAA Study Guide

This guide organizes the note files in `notes/` into a practical study path for AWS Solutions Architect Associate topics.

## 01 - Core Foundations

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | IAM | [IAM](notes/IAM.md) | AWS Organizations, AWS KMS | Identity and permissions drive almost every SAA architecture decision. |
| 2 | AWS Organizations | [Organizations](notes/Organizations.md) | IAM, AWS Config | Multi-account structure is easiest to understand right after identity and access control. |
| 3 | Amazon VPC | [VPC](notes/VPC.md) | Amazon EC2, Elastic Load Balancing | Networking boundaries and subnet design support nearly every hosted workload. |

## 02 - Networking, Routing, and Edge

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon Route 53 | [Route 53](notes/Route%2053.md) | Elastic Load Balancing, Amazon CloudFront | DNS routing is a base concept for highly available and global architectures. |
| 2 | Elastic Load Balancing | [Elastic Load Balancer](notes/Elastic%20Load%20Balancer.md) | Amazon EC2, Amazon Route 53 | Load balancing fits naturally after DNS and before deeper edge services. |
| 3 | Amazon CloudFront | [CloudFront](notes/CloudFront.md) | Amazon S3, AWS WAF | CDN patterns often appear with static content delivery and edge security. |
| 4 | AWS Global Accelerator | [Global Accelerator](notes/Global%20Accelerator.md) | Amazon Route 53, Elastic Load Balancing | It is best learned as a global traffic-routing option alongside DNS and load balancing. |
| 5 | Amazon API Gateway | [API Gateway](notes/API%20Gateway.md) | AWS Lambda, Serverless Architecture | API entry points are a common exam pairing with serverless application design. |
| 6 | AWS Certificate Manager | [ACM](notes/ACM.md) | Amazon CloudFront, AWS WAF | TLS certificate management is a core edge security dependency for public endpoints. |
| 7 | AWS WAF | [WAF](notes/WAF.md) | Amazon CloudFront, AWS Certificate Manager | WAF is usually tested as the web-layer protection choice for internet-facing apps. |
| 8 | AWS Network Firewall | [Network Firewall](notes/Network%20Firewall.md) | Amazon VPC, AWS Site-to-Site VPN | It extends VPC-level traffic inspection and filtering for stricter network controls. |
| 9 | AWS Site-to-Site VPN | [Site-to-Site VPN](notes/Site-to-Site%20VPN.md) | AWS Direct Connect, Amazon VPC | Hybrid connectivity decisions often compare VPN speed, cost, and setup tradeoffs. |
| 10 | AWS Direct Connect | [Direct Connect](notes/Direct%20Connect.md) | AWS Site-to-Site VPN, AWS Outposts | Dedicated private connectivity belongs here with other hybrid network options. |

## 03 - Compute and Application Hosting

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon EC2 | [EC2](notes/EC2.md) | Amazon EBS, Elastic Load Balancing | EC2 is the baseline compute service behind many other SAA scenarios. |
| 2 | Amazon EBS | [EBS](notes/EBS.md) | Amazon EC2, Amazon Backup | EBS is easiest to learn right after EC2 because it is EC2 block storage. |
| 3 | AWS Elastic Beanstalk | [Elastic Beanstalk](notes/Elastic%20Beanstalk.md) | Amazon EC2, Amazon RDS | It introduces managed application hosting without hiding core AWS building blocks. |
| 4 | Amazon ECS | [ECS](notes/ECS.md) | Amazon EC2, Amazon EKS | Container orchestration makes more sense after you know standard compute hosting. |
| 5 | Amazon EKS | [EKS](notes/EKS.md) | Amazon ECS, Amazon VPC | Kubernetes belongs after ECS because both solve container deployment in different ways. |
| 6 | AWS Lambda | [Lambda](notes/Lambda.md) | Amazon API Gateway, Amazon EventBridge | Lambda is central to event-driven and serverless architecture patterns. |
| 7 | Serverless Architecture | [Serverless](notes/Serverless.md) | AWS Lambda, Amazon API Gateway | This note ties together the serverless patterns that combine multiple services in the exam. |

## 04 - Storage and Data Transfer

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon S3 | [S3](notes/S3.md) | Amazon CloudFront, AWS Glue | S3 is the default object storage choice and appears across many AWS architectures. |
| 2 | Amazon EFS | [EFS](notes/EFS.md) | Amazon EC2, Amazon ECS | Shared file storage is commonly compared against S3 and FSx in SAA questions. |
| 3 | Amazon FSx | [FSx](notes/FSx.md) | Amazon EFS, Amazon EC2 | FSx is best studied as the managed file system option for specialized workloads. |
| 4 | AWS Storage Gateway | [Storage Gateway](notes/Storage%20Gateway.md) | AWS DataSync, AWS Snowball | It bridges on-premises systems to AWS storage in hybrid migration scenarios. |
| 5 | AWS DataSync | [DataSync](notes/DataSync.md) | AWS Storage Gateway, AWS Snowball | DataSync is a fast online transfer choice that is often compared with other migration tools. |
| 6 | AWS Snowball | [Snowball](notes/Snowball.md) | AWS DataSync, AWS Storage Gateway | Snowball belongs here because offline data transfer is a classic exam comparison. |

## 05 - Databases and Caching

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon RDS | [RDS](notes/RDS.md) | Amazon Aurora, Amazon EC2 | Managed relational databases should come before AWS-specific database optimizations. |
| 2 | Amazon Aurora | [Aurora](notes/Aurora.md) | Amazon RDS, Amazon ElastiCache | Aurora is easiest to understand once standard RDS concepts are familiar. |
| 3 | Amazon DynamoDB | [DynamoDB](notes/DynamoDB.md) | AWS Lambda, Amazon EventBridge | NoSQL design patterns are a distinct exam area and contrast well with relational services. |
| 4 | Amazon ElastiCache | [ElastiCache](notes/ElastiCache.md) | Amazon RDS, Amazon Aurora | Caching belongs here because the exam often asks when to offload reads from databases. |
| 5 | AWS Database Migration Service | [DMS](notes/DMS.md) | Amazon RDS, Amazon Aurora | Database migration patterns are usually tested alongside target database choices. |

## 06 - Messaging, Streaming, and Event-Driven Architecture

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon SQS | [SQS](notes/SQS.md) | Amazon SNS, Amazon EventBridge | Queueing basics are central to decoupled application design in the SAA exam. |
| 2 | Amazon SNS | [SNS](notes/SNS.md) | Amazon SQS, Amazon EventBridge | Pub/sub delivery is commonly compared against queueing and event bus patterns. |
| 3 | Amazon EventBridge | [EventBridge](notes/EventBridge.md) | AWS Lambda, Amazon SNS | Event buses are best learned after basic queueing and notification patterns. |
| 4 | Amazon Kinesis Data Streams | [Kinesis Data Streams](notes/Kensis%20Data%20Stream.md) | Amazon Kinesis Data Firehose, Amazon SQS | Streaming ingestion belongs here with other event and messaging patterns. |
| 5 | Amazon Kinesis Data Firehose | [Kinesis Data Firehose](notes/Kensis%20Data%20Firehose.md) | Amazon Kinesis Data Streams, Amazon S3 | Firehose is usually tested as the managed delivery option for streaming data. |

## 07 - Security, Encryption, and Identity

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | AWS KMS | [KMS](notes/KMS.md) | IAM, AWS Secrets Manager | Encryption key management is a core security dependency across many AWS services. |
| 2 | AWS Secrets Manager | [Secrets Manager](notes/Secret%20Management%20Service.md) | AWS KMS, Amazon RDS | Secret storage is commonly tested with application and database credential management. |
| 3 | AWS Directory Service | [Directory Service](notes/Directory%20Service.md) | IAM, AWS Organizations | Directory integration belongs here because it supports identity use cases beyond IAM users and roles. |
| 4 | Amazon GuardDuty | [GuardDuty](notes/GuardDuty.md) | AWS CloudTrail, AWS Config | Threat detection fits after the core identity and encryption building blocks. |
| 5 | AWS CloudTrail | [CloudTrail](notes/CloudTrail.md) | AWS Config, Amazon GuardDuty | Audit logging is a frequent exam topic for governance and forensic visibility. |
| 6 | AWS Config | [Config](notes/Config.md) | AWS CloudTrail, AWS Organizations | Config tracks resource compliance and belongs with governance and auditing services. |

## 08 - Monitoring, Management, and Operations

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | Amazon CloudWatch | [CloudWatch](notes/CloudWatch.md) | AWS Lambda, Amazon EC2 | Monitoring, logs, metrics, and alarms are core operational concepts across AWS. |
| 2 | AWS Systems Manager | [Systems Manager](notes/System%20Manager.md) | Amazon EC2, AWS CloudWatch | Operational automation and patching are common EC2 administration exam themes. |
| 3 | AWS Backup | [Backup](notes/Backup.md) | Amazon EBS, Amazon RDS | Centralized backup strategy belongs here because it supports resilience across workloads. |
| 4 | Disaster Recovery | [Disaster Recovery](notes/Disaster%20Recovery.md) | AWS Backup, Amazon Route 53 | DR patterns connect backup, failover, RTO, and RPO decision-making. |

## 09 - Analytics, Data Lake, and Machine Learning

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | AWS Glue | [Glue](notes/Glue.md) | AWS Lake Formation, Amazon S3 | Glue is a common ETL starting point for analytics and data lake architectures. |
| 2 | AWS Lake Formation | [Lake Formation](notes/Lake%20Formation.md) | AWS Glue, Amazon S3 | It belongs here because data lake governance builds on S3 and ETL foundations. |
| 3 | Amazon EMR | [EMR](notes/EMR.md) | AWS Glue, Amazon S3 | Big data processing is easier to place after data lake storage and ingestion concepts. |
| 4 | Amazon SageMaker | [SageMaker](notes/SageMaker.md) | Amazon S3, AWS Glue | SageMaker appears in SAA as a managed ML service that often consumes prepared data. |

## 10 - Hybrid Cloud and Migration

| Order | Service | File | Learn With | Why It Belongs Here |
|---:|---|---|---|---|
| 1 | AWS Outposts | [Outposts](notes/Outposts.md) | AWS Direct Connect, AWS Site-to-Site VPN | Outposts anchors the hybrid section because it extends AWS infrastructure on premises. |
| 2 | AWS Storage Gateway | [Storage Gateway](notes/Storage%20Gateway.md) | AWS DataSync, Amazon S3 | This is a cross-reference to the earlier storage note for hybrid file and backup patterns. |
| 3 | AWS Snowball | [Snowball](notes/Snowball.md) | AWS DataSync, AWS Storage Gateway | This is a cross-reference to the earlier transfer note for offline migration scenarios. |
| 4 | AWS DataSync | [DataSync](notes/DataSync.md) | AWS Storage Gateway, AWS Database Migration Service | This is a cross-reference to the earlier transfer note for online migration patterns. |
| 5 | AWS Database Migration Service | [DMS](notes/DMS.md) | Amazon RDS, AWS DataSync | This is a cross-reference to the earlier database note for migration-focused exam cases. |
| 6 | AWS Direct Connect | [Direct Connect](notes/Direct%20Connect.md) | AWS Site-to-Site VPN, AWS Outposts | This is a cross-reference to the earlier networking note for dedicated hybrid connectivity. |
| 7 | AWS Site-to-Site VPN | [Site-to-Site VPN](notes/Site-to-Site%20VPN.md) | AWS Direct Connect, Amazon VPC | This is a cross-reference to the earlier networking note for quick hybrid connectivity. |