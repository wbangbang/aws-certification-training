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

#### Understand the global infrastructure

#### Understand regions

#### Understand Availability Zones

#### Understand the hybrid deployment model



<span id="chapter-2"></span>
## Chapter 2