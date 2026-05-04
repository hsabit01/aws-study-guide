# AWS Study Guide

Grouped index of AWS service notes in this repository.

## 1. Identity, Access, Certificates & Secrets

| Service | Description |
|---|---|
| [IAM](notes/IAM.md) | Manage AWS users, groups, roles, policies, and permissions. |
| [IAM Identity Center](notes/IAM%20Identity%20Center.md) | Centralized workforce access and single sign-on for AWS accounts and applications. |
| [Amazon Cognito](notes/Amazon%20Cognito.md) | Add user sign-up, sign-in, and access control to web and mobile apps. |
| [Directory Service](notes/Directory%20Service.md) | Managed Microsoft Active Directory and directory integration for AWS workloads. |
| [ACM](notes/ACM.md) | Provision, manage, and renew SSL/TLS certificates for AWS resources. |
| [KMS](notes/KMS.md) | Create and manage encryption keys for protecting data across AWS services. |
| [Secrets Manager](notes/Secrets%20Manager.md) | Store, rotate, and retrieve application secrets such as passwords and API keys. |

## 2. Security, Threat Detection & Compliance

| Service | Description |
|---|---|
| [GuardDuty](notes/GuardDuty.md) | Detect threats and suspicious activity across AWS accounts, workloads, and data. |
| [Amazon Inspector](notes/Amazon%20Inspector.md) | Automatically scan workloads for software vulnerabilities and unintended network exposure. |
| [Amazon Macie](notes/Amazon%20Macie.md) | Discover and protect sensitive data, especially in Amazon S3. |
| [AWS Shield](notes/AWS%20Shield.md) | Protect applications from distributed denial-of-service attacks. |
| [WAF](notes/WAF.md) | Filter and block malicious HTTP and HTTPS web requests. |
| [Network Firewall](notes/Network%20Firewall.md) | Deploy managed network firewall protection for VPC traffic. |
| [CloudTrail](notes/CloudTrail.md) | Record AWS API activity for auditing, governance, and compliance. |
| [Config](notes/Config.md) | Track resource configuration changes and evaluate compliance rules. |

## 3. Compute, Containers & Application Hosting

| Service | Description |
|---|---|
| [EC2](notes/EC2.md) | Run virtual servers in the cloud with flexible instance types and pricing options. |
| [Lambda](notes/Lambda.md) | Run code without managing servers using event-driven serverless functions. |
| [ECS](notes/ECS.md) | Run and manage Docker containers using AWS-native container orchestration. |
| [EKS](notes/EKS.md) | Run managed Kubernetes clusters on AWS. |
| [Elastic Beanstalk](notes/Elastic%20Beanstalk.md) | Deploy and manage applications without manually handling infrastructure. |
| [AWS App Runner](notes/AWS%20App%20Runner.md) | Deploy containerized web applications and APIs from source code or images. |
| [AWS Batch](notes/AWS%20Batch.md) | Run batch computing jobs at scale using managed compute environments. |
| [AWS Auto Scaling](notes/AWS%20Auto%20Scaling.md) | Automatically adjust application capacity based on demand. |
| [AWS Amplify](notes/AWS%20Amplify.md) | Build, deploy, and host full-stack web and mobile applications. |
| [Serverless](notes/Serverless.md) | Design applications using managed services without provisioning or managing servers. |

## 4. Networking, CDN, Edge & Hybrid Connectivity

| Service | Description |
|---|---|
| [VPC](notes/VPC.md) | Create isolated virtual networks for AWS resources. |
| [Elastic Load Balancer](notes/Elastic%20Load%20Balancer.md) | Distribute application traffic across multiple targets for availability and scale. |
| [Route 53](notes/Route%2053.md) | Manage DNS, domain registration, and traffic routing. |
| [CloudFront](notes/CloudFront.md) | Deliver content globally using AWS's content delivery network. |
| [Global Accelerator](notes/Global%20Accelerator.md) | Improve global application availability and performance using AWS edge locations. |
| [Direct Connect](notes/Direct%20Connect.md) | Establish dedicated private network connections from on-premises environments to AWS. |
| [Site-to-Site VPN](notes/Site-to-Site%20VPN.md) | Connect on-premises networks to AWS VPCs using encrypted VPN tunnels. |
| [AWS Outposts](notes/AWS%20Outposts.md) | Run AWS infrastructure and services on-premises for hybrid cloud workloads. |

## 5. Storage, Backup & Data Transfer

| Service | Description |
|---|---|
| [S3](notes/S3.md) | Store and retrieve objects with high durability, scalability, and lifecycle features. |
| [EBS](notes/EBS.md) | Provide block storage volumes for EC2 instances. |
| [EFS](notes/EFS.md) | Provide scalable shared file storage for Linux-based workloads. |
| [FSx](notes/FSx.md) | Run managed file systems such as Windows File Server, Lustre, NetApp ONTAP, and OpenZFS. |
| [Storage Gateway](notes/Storage%20Gateway.md) | Connect on-premises environments to AWS cloud storage. |
| [Backup](notes/Backup.md) | Centrally manage and automate backups across AWS services. |
| [Snowball](notes/Snowball.md) | Transfer large amounts of data using physical edge devices. |
| [DataSync](notes/DataSync.md) | Move data between on-premises storage, edge locations, and AWS storage services. |
| [AWS Transfer Family](notes/AWS%20Transfer%20Family.md) | Transfer files into and out of AWS using SFTP, FTPS, FTP, and AS2. |

## 6. Databases & Caching

| Service | Description |
|---|---|
| [RDS](notes/RDS.md) | Run managed relational databases such as MySQL, PostgreSQL, MariaDB, Oracle, and SQL Server. |
| [Aurora](notes/Aurora.md) | Use AWS's cloud-optimized relational database compatible with MySQL and PostgreSQL. |
| [DynamoDB](notes/DynamoDB.md) | Use a fully managed NoSQL key-value and document database. |
| [ElastiCache](notes/ElastiCache.md) | Add managed in-memory caching using Redis or Memcached. |
| [Amazon DocumentDB](notes/Amazon%20DocumentDB.md) | Run a managed document database compatible with MongoDB workloads. |
| [Amazon Keyspaces](notes/Amazon%20Keyspaces.md) | Run managed Apache Cassandra-compatible wide-column databases. |
| [Amazon Neptune](notes/Amazon%20Neptune.md) | Run managed graph databases for highly connected data. |
| [Amazon Timestream](notes/Amazon%20Timestream.md) | Store and analyze time-series data from applications, IoT, and operations. |

## 7. Analytics, Data Lake, Search & BI

| Service | Description |
|---|---|
| [Amazon Athena](notes/Amazon%20Athena.md) | Query data in Amazon S3 using SQL without managing servers. |
| [Glue](notes/Glue.md) | Discover, prepare, catalog, and transform data for analytics. |
| [EMR](notes/EMR.md) | Run big data frameworks such as Apache Spark, Hive, and Presto. |
| [Amazon Redshift](notes/Amazon%20Redshift.md) | Analyze data using a managed cloud data warehouse. |
| [Amazon OpenSearch Service](notes/Amazon%20OpenSearch%20Service.md) | Search, analyze, and visualize log and application data. |
| [Amazon QuickSight](notes/Amazon%20QuickSight.md) | Create business intelligence dashboards and data visualizations. |
| [Lake Formation](notes/Lake%20Formation.md) | Build, secure, and manage data lakes on AWS. |
| [SageMaker](notes/SageMaker.md) | Build, train, and deploy machine learning models. |

## 8. Messaging, Streaming, Events & Workflows

| Service | Description |
|---|---|
| [SQS](notes/SQS.md) | Decouple applications using managed message queues. |
| [SNS](notes/SNS.md) | Send pub/sub notifications to applications, users, and services. |
| [Amazon SES](notes/Amazon%20SES.md) | Send and receive email using a scalable email service. |
| [EventBridge](notes/EventBridge.md) | Build event-driven applications using event buses and routing rules. |
| [AWS Step Functions](notes/AWS%20Step%20Functions.md) | Coordinate distributed workflows using visual state machines. |
| [Amazon MQ](notes/Amazon%20MQ.md) | Run managed message brokers for ActiveMQ and RabbitMQ. |
| [Amazon MSK](notes/Amazon%20MSK.md) | Run managed Apache Kafka streaming clusters. |
| [Kinesis Data Streams](notes/Kinesis%20Data%20Streams.md) | Capture and process real-time streaming data. |
| [Kinesis Data Firehose](notes/Kinesis%20Data%20Firehose.md) | Deliver streaming data to destinations such as S3, Redshift, OpenSearch, and third-party tools. |
| [API Gateway](notes/API%20Gateway.md) | Create, publish, secure, and monitor APIs at scale. |
| [AWS AppFlow](notes/AWS%20AppFlow.md) | Transfer data between SaaS applications and AWS services. |

## 9. Migration, Disaster Recovery & Resilience

| Service | Description |
|---|---|
| [AWS Application Migration Service](notes/AWS%20Application%20Migration%20Service.md) | Migrate applications to AWS with minimal downtime. |
| [DMS](notes/DMS.md) | Migrate databases to AWS with support for homogeneous and heterogeneous migrations. |
| [AWS Elastic Disaster Recovery](notes/AWS%20Elastic%20Disaster%20Recovery.md) | Replicate and recover servers into AWS for disaster recovery. |
| [Disaster Recovery](notes/Disaster%20Recovery.md) | Plan recovery strategies for workloads, data, and infrastructure failures. |

## 10. Management, Governance, Operations & Optimization

| Service | Description |
|---|---|
| [Organizations](notes/Organizations.md) | Centrally manage multiple AWS accounts and apply governance controls. |
| [AWS CloudFormation](notes/AWS%20CloudFormation.md) | Define and provision AWS infrastructure using templates. |
| [CloudWatch](notes/CloudWatch.md) | Monitor metrics, logs, alarms, and operational events. |
| [Systems Manager](notes/Systems%20Manager.md) | Manage, patch, automate, and operate AWS and hybrid resources. |
| [AWS Compute Optimizer](notes/AWS%20Compute%20Optimizer.md) | Recommend optimal compute resources based on utilization patterns. |
| [Trusted Advisor](notes/Trusted%20Advisor.md) | Review AWS environments for cost, security, performance, fault tolerance, and service limits. |
| [AWS Well-Architected Tool](notes/AWS%20Well-Architected%20Tool.md) | Review workloads against AWS Well-Architected best practices. |
