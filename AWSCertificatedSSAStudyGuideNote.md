# AWS Certificated SSA Study Guide Note

## Objective Map

### Domains

| No. | Domain                                                                                    | Percentage |
| :-: | :---------------------------------------------------------------------------------------- | :--------- |
| 1   | [Designing highly available, cost-efficient, faulttolerant, scalable systems](#domain-1)  | 60%        |
| 2   | [Implementation/Deployment](#domain-2)                                                    | 20%        |
| 3   | [Data Security](#domain-3)                                                                | 10%        |
| 4   | [Troubleshooting](#domain-4)                                                              | 10%        |      

### Domains' Objectives

<span id="domain-1"></span>
#### Domain 1
Identify and recognize cloud architecture considerations, such as fundamental components and effective designs. 
         
| Content                      | Chapters      |
| :--------------------------- | :------------ |
| How to design cloud services | []() []()     |
| Planning and design          | []() []()     |
| Monitoring and logging       | []() []()     |
| Familiarity with:            |               |
| + Best practices for AWS architecture  |        
| + Developing to client specifications, including pricing/cost (e.g., onDemand vs. Reserved vs. Spot; RTO and RPO DR Design) |             
| + Architectural trade-off decisions (e.g., high availability vs. cost, Amazon Relational Database Service (RDS) vs. installing your own database on Amazon Elastic Compute Cloud (EC2)) |      
| + Hybrid IT architectures (e.g., Direct Connect, Storage Gateway, VPC, Directory Services) |        
| + Elasticity and scalability (e.g., Auto Scaling, SQS, ELB, CloudFront) |         

<span id="domain-2"></span>
#### Domain 2

Identify the appropriate techniques and methods using Amazon EC2, Amazon S3, AWS Elastic Beanstalk, AWS CloudFormation, AWS OpsWorks, Amazon Virtual Private Cloud (VPC), and AWS Identity and Access Management (IAM) to code and implement a cloud solution.

| Content                                                            | Chapters      |
| :----------------------------------------------------------------- | :------------ |
| Configure an Amazon Machine Image (AMI)                            |
| Operate and extend service management in a hybrid IT architecture  |
| Configure services to support compliance requirements in the cloud |
| Launch instances across the AWS global infrastructure              |
| Configure IAM policies and best practices                          |


<span id="domain-3"></span>
#### Domain 3

* Recognize and implement secure practices for optimum cloud deployment and maintenance.

| Content                                                                     | Chapters      |
| :-------------------------------------------------------------------------- | :------------ |
| AWS shared responsibility model                                             |
| AWS platform compliance                                                     |
| AWS security attributes (customer workloads down to physical layer)         |
| AWS administration and security services                                    |
| AWS Identity and Access Management (IAM)                                    |
| Amazon Virtual Private Cloud (VPC)                                          |
| AWS CloudTrail                                                              |
| Ingress vs. egress filtering, and which AWS services and features fit       |
| “Core” Amazon EC2 and S3 security feature sets                              |
| Incorporating common conventional security products (Firewall, VPN)         |
| Design patterns                                                             |
| DDoS mitigation                                                             |
| Encryption solutions (e.g., key services)                                   |
| Complex access controls (building sophisticated security groups, ACLs, etc.)|
| Amazon CloudWatch for the security architect                                |
| Trusted Advisor                                                             |
| CloudWatch Logs                                                             |

* Recognize critical disaster recovery techniques and their
implementation.

| Content                      | Chapters      |
| :--------------------------- | :------------ |
| Disaster recovery            
| Recovery time objective
| Recovery point objective
| Amazon Elastic Block Store
| AWS Import/Export
| AWS Storage Gateway
| Amazon Route53
| Validation of data recovery method

<span id="domain-4"></span>
#### Domain 4 

| Content                                           | Chapters      |
| :------------------------------------------------ | :------------ |
| General troubleshooting information and questions |               |    




<span id="chapter-1"></span>
## Chapter 1 - Introduction to AWS

### What Is Cloud Computing?

#### Advantages of Cloud Computing

Six advantages:

1. Variables vs. Capital Expense
2. Economies of Scale
3. Stop Guessing Capacity
4. Increase Speed and Agility
5. Focus on Business Differentiators
6. Go Global in Minutes

#### Cloud Computing Deployment Models

Two models the exam focuses on:

1. all-in cloud-based deployments
2. hybrid deployments

### AWS Fundamentals

AWS global infrastructure and AWS approach to security and compliance are key foundational concepts to understand for the exam. 

#### Global Infrastructure

Two concepts: **Region** and **Availability Zone**

> Tip: You can achieve high availability by deploying your application across multiple Availability Zones. Redundant instances for each tier (for example, web, application, and database) of an application should be placed in distinct Availability Zones, thereby creating a multisite solution. At a minimum, the goal is to have an independent copy of each application stack in two or more Availability Zones.


#### Security and Compliance

> Tip: Organizations retain complete control and ownership over the region in which their data is physically located, allowing them to meet regional compliance and data residency requirements.

### AWS Cloud Computing Platform

![]()

#### Accessing the Platform

To access AWS Cloud services, three ways:

1. AWS Management Console
2. AWS Command Line Interface (CLI)
3. AWS Software Development Kits (SDKs)

#### Compute and Networking Services

* Amazon Elastic Compute Cloud (Amazon EC2)
* AWS Lambda
* Auto Scaling
* Elastic Load Balancing
* AWS Elastic Beanstalk
* Amazon Virtual Private Cloud (Amazon VPC)
* AWS Direct Connect
* Amazon Route 53

#### Storage and Content Delivery

* Amazon Simple Storage Service (Amazon S3)
* Amazon Glacier
* Amazon Elastic Block Store (Amazon EBS)
* AWS Storage Gateway
* Amazon CloudFront

#### Database Services

* Amazon Relational Database Service (Amazon RDS)
* Amazon DynamoDB
* Amazon Redshift
* Amazon ElastiCache

#### Management Tools

* Amazon CloudWatch
* AWS CloudFormation
* AWS CloudTrail
* AWS Config

#### Security and Identity

* AWS Identity and Access Management (IAM)
* AWS Key Management Service (KMS)
* AWS Directory Service
* AWS Certificate Manager
* AWS Web Application Firewall (WAF)

#### Application Services

* Amazon API Gateway
* Amazon Elastic Transcoder
* Amazon Simple Notification Service (Amazon SNS)
* Amazon Simple Email Service (Amazon SES)
* Amazon Simple Workflow Service (Amazon SWF)
* Amazon Simple Queue Service (Amazon SQS)

### Exam Essentials

* Understand the global infrastructure
* Understand regions
* Understand Availability Zones
* Understand the hybrid deployment model



<span id="chapter-2"></span>
## Chapter 2 - Amazon Simple Storage Service (Amazon S3) and Amazon Glacier Storage

### Introduction

Common use cases for S3:

* Backup and archive for on-premises or cloud data
* Content, media, and software storage and distribution
* Big data analytics
* Static website hosting
* Cloud-native mobile and Internet application hosting
* Disaster recovery

### Object Storage versus Traditional Block and File Storage

Instead of being closely associated with a server, Amazon S3 storage is independent of a server and is accessed over the Internet - data is managed as objects using an Application Program Interface (API) built on standard HTTP verbs.

Each Amazon S3 object contains both data and metadata. Objects reside in containers called buckets, and each object is identified by a unique user-specified key (filename). Buckets are a simple flat folder *with no file system hierarchy*. That is, you can have multiple buckets, but you can’t have a sub-bucket within a bucket. Each bucket can hold an unlimited number of objects.

In Amazon S3, you GET an object or PUT an object, operating on the whole object at once, instead of incrementally updating portions of the object as you would with a file.

> Tip: If you need traditional block or file storage in addition to Amazon S3 storage, AWS provides options. The Amazon EBS service provides block level storage for Amazon Elastic Compute Cloud (Amazon EC2) instances. Amazon Elastic File System (AWS EFS) provides network-attached shared file storage (NAS storage) using the NFS v4 protocol.

### Amazon Simple Storage Service (Amazon S3) Basics

#### Buckets

Bucket names can contain up to 63 lowercase letters, numbers, hyphens, and periods. You can create and use multiple buckets; you can have up to 100 per account by default.

> Tip: It is a best practice to use bucket names that contain your domain name and conform to the rules for DNS names. This ensures that your bucket names are your own, can be used in all regions, and can host static websites.

#### AWS Regions

#### Objects

Objects can range in size from 0 bytes up to 5TB, and a single bucket can store an unlimited number of objects.

#### Keys

A key can be up to 1024 bytes of Unicode UTF-8 characters, including embedded slashes, backslashes, dots, and dashes.

Keys must be unique within a single bucket, but different buckets can contain objects with the same key. The combination of bucket, key, and optional version ID uniquely identifies an Amazon S3 object.

#### Object URL

> Tip: For convenience, the Amazon S3 console and the Prefix and Delimiter feature allow you to navigate within an Amazon S3 bucket as if there were a folder hierarchy. However, remember that a bucket is a single flat namespace of keys with no structure.

#### Amazon S3 Operations

#### REST Interface

> Tip: Always use HTTPS for Amazon S3 API requests to ensure that your requests and data are secure.

> Tip: Amazon S3 originally supported a SOAP (Simple Object Access Protocol) API in addition to the REST API, but you should use the REST API. The legacy HTTPS endpoint is still available, but new features are not supported.

#### Durability and Availability

> Tip: Even though Amazon S3 storage offers very high durability at the infrastructure level, it is still a best practice to protect against user-level accidental deletion or overwriting of data by using additional features such as versioning, cross-region replication, and MFA Delete.

#### Data Consistency

Amazon S3 is an **eventually consistent** system.

#### Access Control

Amazon S3 provides both coarse-grained access controls (Amazon S3 Access Control Lists [ACLs]), and fine-grained
access controls (Amazon S3 bucket policies, AWS Identity and Access Management [IAM] policies, and query-string authentication).

Differences between bucket policies and IAM:

* They are associated with the bucket resource instead of an IAM principal.
* They include an explicit reference to the IAM principal in the policy. This principal can be associated with a different AWS account, so Amazon S3 bucket policies allow you to assign cross-account access to Amazon S3 resources.

#### Static Website Hosting

### Amazon S3 Advanced Features

#### Prefixes and Delimiters

> Tip: Use delimiters and object prefixes to hierarchically organize the objects in your Amazon S3 buckets, but always remember that Amazon S3 is not really a file system.

#### Storage Classes

Amazon Glacier allows you to retrieve up to 5% of the Amazon S3 data stored in Amazon Glacier for free each month.

> Tip: Set a data retrieval policy to limit restores to the free tier or to a maximum GBper-hour limit to avoid or minimize Amazon Glacier restore fees.

#### Object Lifecycle Management

#### Encryption

To encrypt your Amazon S3 data in flight, you can use the Amazon S3 Secure Sockets Layer (SSL) API endpoints. This ensures that all data sent to and from Amazon S3 is encrypted while in transit using the HTTPS protocol.

To encrypt your Amazon S3 data at rest, you can use several variations of Server-Side Encryption (SSE). Amazon S3 encrypts your data at the object level as it writes it to disks in its data centers and decrypts it for you when you access it. All SSE performed by Amazon S3 and AWS Key Management Service (Amazon KMS) uses the 256-bit Advanced Encryption Standard (AES). 

##### SSE-S3 (AWS-Managed Keys)
##### SSE-KMS (AWS KMS Keys)
##### SSE-C (Customer-Provided Keys)
##### Client-Side Encryption

> Tip: For maximum simplicity and ease of use, use server-side encryption with AWSmanaged
keys (SSE-S3 or SSE-KMS).

#### Versioning

#### Pre-Signed URLs

#### Multipart Upload

> Tip: You can set an object lifecycle policy on a bucket to abort incomplete multipart uploads after a specified number of days. This will minimize the storage costs associated with multipart uploads that were not completed.

#### Range GETs

#### Cross-Region Replication

> Tip: If turned on in an existing bucket, cross-region replication will only replicate new objects. Existing objects will not be replicated and must be copied to the new bucket via a separate command.

#### Logging

Logging is off by default.

#### Event Notifications

#### Best Practices, Patterns, and Performance

> Tip: If you are using Amazon S3 in a GET-intensive mode, such as a static website hosting, for best performance you should consider using an Amazon CloudFront distribution as a caching layer in front of your Amazon S3 bucket.

### Amazon Glacier

#### Archives

An archive can contain up to 40TB of data, and you can have an unlimited number of archives.

#### Vaults

Vaults are containers for archives. Each AWS account can have up to 1,000 vaults.

#### Vaults Locks

#### Data Retrieval

#### Amazon Glacier versus Amazon Simple Storage Service (Amazon S3)

### Exam Essentials

* Know what amazon s3 is and what it is commonly used for. 
* Understand how object storage differs from block and file storage.
* Understand the basics of Amazon S3.
* Understand the durability, availability, and data consistency model of Amazon S3.
* Know how to enable static website hosting on Amazon S3.
* Know how to protect your data on Amazon S3.
* Know the use case for each of the Amazon S3 storage classes.
* Know how to use lifecycle configuration rules. 
* Know how to use Amazon S3 event notifications. 
* Know the basics of amazon glacier as a standalone service.



<span id="chapter-3"></span>
## Chapter 3 - Amazon Elastic Compute Cloud (Amazon EC2) and Amazon Elastic Block Store (Amazon EBS)

### Amazon Elastic Compute Cloud (Amazon EC2)

#### Compute Basics

There are two concepts that are key to launching instances on AWS: (1) the amount of virtual hardware dedicated to the instance and (2) the software loaded on the instance. These two dimensions of new instances are controlled, respectively, by the instance type and the AMI.

##### Instance Types

##### Amazon Machine Images (AMIs)

The Amazon Machine Image (AMI) defines the initial software that will be on an instance when it is launched.

Four sources of AMIs:

* Published by AWS
* The AWS Marketplace
* Generated from Existing Instances
* Uploaded Virtual Servers

#### Securely Using an Instance

##### Addressing an Instance

Few ways that an instance may be addressed over the web upon creation:

* Public Domain Name System (DNS) Name
* Public IP
* Elastic IP

> Tip: Private IP addresses and Elastic Network Interfaces (ENIs) are additional methods of addressing instances that are available in the context of an Amazon VPC.

##### Initial Access

Key pairs: public key & private key.

> Tip: Store your private keys securely. When Amazon EC2 launches a Linux instance, the public key is stored in the /.ssh/authorized_keys file on the instance and an initialuser is created. The initial user can vary depending on the OS. For example, the Amazon Linux distribution initial user is ec2-user. Initial access to the instance is obtained by using the ec2-user and the private key to log in via SSH. At this point, you can configure other users and enroll in a directory such as LDAP.

##### Virtual Firewall Protection

AWS allows you to control traffic in and out of your instances through virtual firewalls called security groups.

| Type of Security            | Group Capabilities                            |
| :-------------------------- | :-------------------------------------------- |
| EC2-Classic Security Groups | Control outgoing instance traffic             |
| VPC Security Groups         | Control outgoing and incoming instance traffic|

A security group is default deny; that is, it does not allow any traffic that is not explicitly allowed by a security group rule.

A security group is a stateful firewall; that is, an outgoing message is remembered so that the response is allowed through the security group without an explicit inbound rule being required.

Security groups are applied at the instance level.

#### The Lifecycle of Instances

##### Launching

##### Managing Instances

Tags are key/value pairs you can associate with your instance or other service. 

##### Monitoring Instances

AWS CloudWatch

##### Modifying an Instance

##### Termination Protection

#### Options

##### Pricing Options

* On-Demand Instances
* Reserved Instances
* Spot Instances

Architectures with Different Pricing Models

##### Tenancy Options

* Shared Tenancy
* Dedicated Instances
* Dedicated Host

##### Placement Groups

#### Instance Stores

### Amazon Elastic Block Store (Amazon EBS)

#### Elastic Block Store Basics

#### Types of Amazon EBS Volumes

##### Magnetic Volumes

A magnetic Amazon EBS volume can range in size from 1 GB to 1 TB and will average 100
IOPS, but has the ability to burst to hundreds of IOPS. They are best suited for:

* Workloads where data is accessed infrequently
* Sequential reads
* Situations where low-cost storage is a requirement

##### General-Purpose SSD

A general-purpose SSD volume can range in size from 1 GB to 16 TB and provides a baseline performance of three IOPS per gigabyte provisioned, capping at 10,000 IOPS. 

General-purpose SSD volumes under 1 TB also feature the ability to burst to up to 3,000 IOPS for extended periods of time.

They are suited for a wide range of workloads where the very highest disk performance is not critical, such as:

* System boot volumes
* Small- to medium-sized databases
* Development and test environments

##### Provisioned IOPS SSD

A Provisioned IOPS SSD volume can range in size from 4 GB to 16 TB. When you provision a Provisioned IOPS SSD volume, you specify not just the size, but also the desired number of IOPS, up to the lower of the maximum of 30 times the number of GB of the volume, or 20,000 IOPS.

Provisioned IOPS SSD volumes provide predictable, high performance and are well suited for:

* Critical business applications that require sustained IOPS performance
* Large database workloads

> Tip: At the time of this writing, AWS released two new HDD volume types: Throughput-Optimized HDD and Cold HDD. Over time, it is expected that these new types will eclipse the current magnetic volume type, fulfilling the needs of any workload requiring HDD performance.
Throughput-Optimized HDD volumes are low-cost HDD volumes designed for frequentaccess, throughput-intensive workloads such as big data, data warehouses, and log processing. Volumes can be up to 16 TB with a maximum IOPS of 500 and maximum throughput of 500 MB/s. These volumes are significantly less expensive than generalpurpose SSD volumes.
Cold HDD volumes are designed for less frequently accessed workloads, such as colder data requiring fewer scans per day. Volumes can be up to 16 TB with a maximum IOPS of 250 and maximum throughput of 250 MB/s. These volumes are significantly less expensive than Throughput-Optimized HDD volumes.

##### Amazon EBS-Optimized Instances

#### Protecting Data

##### Backup/Recovery (Snapshots)

##### Recovering Volumes

##### Encryption Options

When you launch an encrypted Amazon EBS volume, Amazon uses the AWS Key Management Service (KMS) to handle key management.

### Exam Essentials

* Know the basics of launching an Amazon ec2 instance.
* Know what architectures are suited for what Amazon ec2 pricing options
* Know how to combine multiple pricing options that result in cost optimization and scalability.
* Know the benefits of enhanced networking.
* Know the capabilities of vm import/export.
* Know the methods for accessing an instance over the internet. 
* Know the lifetime of an instance store.
* Know the properties of the Amazon EC2 pricing options.
* Know what determines network performance.
* Know what instance metadata is and how it’s obtained. 
* Know how security groups protect instances.
* Know how to interpret the effect of security groups.
* Know the different Amazon ebs volume types, their characteristics, and their appropriate workloads.
* Know how to encrypt an Amazon ebs volume.
* Understand the concept and process of snapshots.
* Know how Amazon ebs-optimized instances affect Amazon ebs performance.



<span id="chapter-4"></span>
## Chapter 4 - Amazon Virtual Private Cloud (Amazon VPC)

### Amazon Virtual Private Cloud (Amazon VPC)

Amazon VPC is the networking layer for Amazon Elastic Compute Cloud (Amazon EC2), and it allows you to build your own virtual network within AWS.

Within a region, you can create multiple Amazon VPCs, and each Amazon VPC is logically isolated even if it shares its IP address space.

When you create an Amazon VPC, you must specify the IPv4 address range by choosing a Classless Inter-Domain Routing (CIDR) block.

The Amazon VPC service was released after the Amazon EC2 service; because of this, there are two different networking platforms available within AWS: EC2-Classic and EC2-VPC.

An Amazon VPC consists of the following components:

* Subnets
* Route tables
* Dynamic Host Configuration Protocol (DHCP) option sets
* Security groups
* Network Access Control Lists (ACLs)

An Amazon VPC has the following optional components:

* Internet Gateways (IGWs)
* Elastic IP (EIP) addresses
* Elastic Network Interfaces (ENIs)
* Endpoints
* Peering
* Network Address Translation (NATs) instances and NAT gateways
* Virtual Private Gateway (VPG), Customer Gateways (CGWs), and Virtual Private Networks (VPNs)

### Subnets

