# AWS Fundamentals

## 1. AWS Basics & Understanding of IaaS, PaaS, SaaS
### Overview of AWS Cloud Computing
- Introduction to AWS and its global infrastructure
- Key AWS services and their use cases
- Benefits of using AWS: scalability, flexibility, security, and cost-effectiveness

### Understanding Cloud Service Models
- **Infrastructure as a Service (IaaS):** Compute, storage, and networking resources (e.g., EC2, S3)
- **Platform as a Service (PaaS):** Managed environments for application development (e.g., AWS Elastic Beanstalk)
- **Software as a Service (SaaS):** Fully managed applications over the internet (e.g., Amazon WorkDocs)

## 2. AWS Storage Services
### Amazon S3 (Simple Storage Service)
- Object storage service for scalable and secure data storage
- Features: Versioning, Lifecycle policies, Cross-region replication, S3 Glacier for archiving
- Use cases: Backup & restore, data lakes, web hosting, and application data storage

### Amazon EFS (Elastic File System)
- Scalable, elastic, and managed file storage for AWS
- Features: NFS protocol support, dynamic scaling, performance modes (General Purpose & Max I/O)
- Use cases: File sharing, big data analytics, and web content management

## 3. Amazon SQS (Simple Queue Service)
- Fully managed message queuing service
- Features: Standard and FIFO queues, message retention, delay queues, and Dead Letter Queues (DLQ)
- Use cases: Decoupling microservices, event-driven architectures, and distributed workloads

## 4. AWS Database Services
### Amazon RDS (Relational Database Service)
- Managed relational database service for structured data storage
- Supported database engines:
  - **Amazon Aurora** (MySQL & PostgreSQL-compatible, high performance)
  - **MySQL & PostgreSQL** (popular open-source databases)
  - **Oracle & SQL Server** (enterprise databases for legacy applications)

### Amazon DynamoDB
- NoSQL database for key-value and document data storage
- Features: Single-digit millisecond latency, global tables, auto-scaling, and on-demand backups
- Use cases: Mobile apps, gaming, IoT, and real-time analytics

## 5. AWS Security & Secrets Management
### AWS Secrets Manager
- Secure storage and retrieval of API keys, credentials, and other secrets
- Features: Automatic secret rotation, fine-grained access control with IAM, and audit logs
- Use cases: Secure database credentials, API keys, and encryption keys

### AWS Key Management Service (KMS)
- Centralized management of cryptographic keys
- Features: Encryption, key rotation, AWS CloudTrail integration for logging
- Use cases: Encrypting S3 objects, RDS instances, and application data

## 6. AWS Lambda: Serverless Computing
- Event-driven serverless compute service
- Writing and managing functions in supported languages: Python, Node.js, Java, Go, etc.
- Key features: Auto-scaling, pay-per-use pricing, triggers from AWS services (S3, DynamoDB, SNS, etc.)
- Use cases: Real-time file processing, chatbots, API backends, and automation scripts
