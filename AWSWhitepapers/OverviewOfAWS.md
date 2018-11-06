# Overview of Amazon Web Services

Source: https://d0.awsstatic.com/whitepapers/aws-overview.pdf

## Types of Cloud Computing

### Cloud Computing Models

**Infrastructure as a Service (IaaS)**
Infrastructure as a Service (IaaS) contains the basic building blocks for cloud IT and typically provide access to networking features, computers (virtual or on dedicated hardware), and data storage space.

**Platform as a Service (PaaS)**
Platform as a Service (PaaS) removes the need for your organization to manage the underlying infrastructure (usually hardware and operating systems) and allows you to focus on the deployment and management of your applications.

**Software as a Service (SaaS)**
With a SaaS offering you do not have to think about how the service is maintained or how the underlying infrastructure is managed; you only need to think about how you will use that particular piece of software.

### Cloud Computing Deployment Models

**Cloud**
A cloud-based application is fully deployed in the cloud and all parts of the application run in the cloud.

**Hybrid**
A hybrid deployment is a way to connect infrastructure and applications between cloud-based resources and existing resources that are not located in the cloud.

**On-premises**
The deployment of resources on-premises, using virtualization and resource management tools, is sometimes called the “private cloud.”

## Amazon Web Services Cloud Platform

### Compute Services

#### Amazon EC2

##### Benefits

* Elastic Web-Scale Computing
* Completely Controlled
* Flexible Cloud Hosting Services
* Integrated
* Reliable
* Secure
	* Located in a VPC with an IP address range.
	* Security Groups and ACLs.
	* VPN connect your existing IT infrastructure to resources in your VPC.
	* Dedicated Instances are Amazon EC2 instances that run on hardware dedicated to a single customer for additional isolation.
	* Dedicated Hosts are physical servers with EC2 instance capacity fully dedicated to your use.
* Inexpensive
	* On-Demand/Reserved/Spot.

#### Amazon EC2 Container Service

Amazon EC2 Container Service (ECS) is a highly scalable, high-performance container management service that supports Docker containers.	

#### Amazon EC2 Container Registry

Amazon EC2 Container Registry (ECR) is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. Amazon ECR is integrated with Amazon EC2 Container Service (ECS). Amazon ECR hosts your images in a highly available and scalable architecture, allowing you to reliably deploy containers for your applications.

#### Amazon Lightsail

Amazon Lightsail is designed to be the easiest way to launch and manage a virtual private server with AWS. Lightsail plans include everything you need to jumpstart your project – a virtual machine, SSDbased storage, data transfer, DNS management, and a static IP address – for a low, predictable price.

#### AWS Batch

AWS Batch enables developers, scientists, and engineers to easily and efficiently run hundreds of thousands of batch computing jobs on AWS.

#### AWS Elastic Beanstalk

AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services. You can simply upload your code, and AWS Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, and auto scaling to application health monitoring. At the same time, you retain full control over the AWS resources powering your application and can access the underlying resources at any time.

#### AWS Lambda

AWS Lambda lets you run code without provisioning or managing servers.

#### Auto Scaling

Auto Scaling helps you maintain application availability and allows you to scale your Amazon EC2 capacity up or down automatically according to conditions that you define.

### Storage

#### Amazon S3

You can use Amazon S3 as primary storage for cloud-native applications; as a bulk repository, or "data lake," for analytics; as a target for backup and recovery and disaster recovery; and with serverless computing. 

#### Amazon Elastic Block Store

Amazon Elastic Block Store (Amazon EBS) provides persistent block storage volumes for use with Amazon EC2 instances in the AWS Cloud. Each Amazon EBS volume is automatically replicated within its Availability Zone to protect you from component failure, offering high availability and durability.

#### Amazon Elastic File System

When mounted on Amazon EC2 instances, an Amazon EFS file system provides a standard file system interface and file system access semantics, allowing you to seamlessly integrate Amazon EFS with your existing applications and tools. Multiple EC2 instances can access an Amazon EFS file system at the same time, allowing Amazon EFS to provide a common data source for workloads and applications running on more than one EC2 instance.

#### Amazon Glacier

Amazon Glacier is a secure, durable, and extremely low-cost storage service for data archiving and longterm backup.

#### AWS Storage Gateway

The AWS Storage Gateway service seamlessly enables hybrid storage between on-premises storage environments and the AWS Cloud.

### Database

#### Amazon Aurora

Amazon Aurora is a MySQL and PostgreSQL compatible relational database engine that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases. 

#### Amazon RDS

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud.

#### Amazon DynamoDB

Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale.

#### Amazon ElastiCache

Amazon ElastiCache is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud.

### Migration

#### AWS Application Discovery Service

AWS Application Discovery Service helps systems integrators quickly and reliably plan application migration projects by automatically identifying applications running in on-premises data centers, their associated dependencies, and their performance profiles.

#### AWS Database Migration Service

The AWS Database Migration Service can migrate your data to and from most widely used commercial and open-source databases. The service supports homogenous migrations as well as heterogeneous migrations between different database platforms. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.

#### AWS Server Migration Service

AWS Server Migration Service (SMS) is an agentless service which makes it easier and faster for you to migrate thousands of on-premises workloads to AWS.

#### AWS Snowball

AWS Snowball is a petabyte-scale data transport solution that uses secure appliances to transfer large amounts of data into and out of AWS. 

#### AWS Snowball Edge

AWS Snowball Edge is a 100 TB data transfer device with on-board storage and compute capabilities. You can use Snowball Edge to move large amounts of data into and out of AWS, as a temporary storage tier for large local datasets, or to support local workloads in remote or offline locations.

#### AWS Snowmobile

AWS Snowmobile is an exabyte-scale data transfer service used to move extremely large amounts of data to AWS. 

### Networking and Content Delivery

#### Amazon VPC

Amazon Virtual Private Cloud (Amazon VPC) lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

#### Amazon CloudFront

Amazon CloudFront is a global content delivery network (CDN) service that accelerates delivery of your websites, APIs, video content, or other web assets.

#### Amazon Route 53

Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service.

#### AWS Direct Connect

AWS Direct Connect makes it easy to establish a dedicated network connection from your premises to AWS.

#### Elastic Load Balancing

Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple EC2 instances. Elastic Load Balancing offers two types of load balancers that both feature high availability, automatic scaling, and robust security. These include the Classic Load Balancer that routes traffic based on either application or network level information, and the Application Load Balancer that routes traffic based on advanced application-level information that includes the content of the request.

### Developer Tools

#### AWS CodeCommit

AWS CodeCommit is a fully managed source control service that makes it easy for companies to host secure and highly scalable private Git repositories.

#### AWS CodeBuild

AWS CodeBuild is a fully managed build service that compiles source code, runs tests, and produces software packages that are ready to deploy.

#### AWS CodeDeploy

AWS CodeDeploy is a service that automates code deployments to any instance, including EC2 instances and instances running on premises.

#### AWS CodePipeline

CodePipeline builds, tests, and deploys your code every time there is a code change, based on the release process models you define. 

#### AWS X-Ray

AWS X-Ray helps developers analyze and debug distributed applications in production or under development, such as those built using a microservices architecture. With X-Ray, you can understand how your application and its underlying services are performing so you can identify and troubleshoot the root cause of performance issues and errors.

### Management Tools

#### Amazon CloudWatch

Amazon CloudWatch is a monitoring service for AWS Cloud resources and the applications you run on AWS. You can use Amazon CloudWatch to collect and track metrics, collect and monitor log files, set alarms, and automatically react to changes in your AWS resources.

#### Amazon EC2 Systems Manager

Amazon EC2 Systems Manager is a management service that helps you automatically collect software inventory, apply operating system (OS) patches, create system images, and configure Windows and Linux operating systems.

#### AWS CloudFormation

You can use the AWS CloudFormation sample templates or create your own templates to describe your AWS resources, and any associated dependencies or runtime parameters, required to run your application.

#### AWS CloudTrail

AWS CloudTrail is a web service that records AWS API calls for your account and delivers log files to you.

#### AWS Config

AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance. The Config Rules feature enables you to create rules that automatically check the configuration of AWS resources recorded by AWS Config.

#### AWS OpsWorks

AWS OpsWorks is a configuration management service that uses Chef, an automation platform that treats server configurations as code. OpsWorks uses Chef to automate how servers are configured, deployed, and managed across your EC2 instances or on-premises compute environments. 

#### AWS Service Catalog

AWS Service Catalog allows organizations to create and manage catalogs of IT services that are approved for use on AWS.

#### AWS Trusted Advisor

Trusted Advisor provides real-time guidance to help you provision your resources following AWS best practices.

#### AWS Personal Health Dashboard

AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that might affect you.

#### AWS Managed Services

AWS Managed Services automates common activities such as change requests, monitoring, patch management, security, and backup services, and provides full-lifecycle services to provision, run, and support your infrastructure. 

### Security, Identity, and Compliance

#### Amazon Cloud Directory

Amazon Cloud Directory enables you to build flexible, cloud-native directories for organizing hierarchies of data along multiple dimensions. While traditional directory solutions, such as Active Directory Lightweight Directory Services (AD LDS) and other LDAP-based directories, limit you to a single hierarchy, Cloud Directory offers you the flexibility to create directories with hierarchies that span multiple dimensions. 

#### AWS Identity and Access Management

AWS Identity and Access Management (IAM) enables you to securely control access to AWS services and resources for your users. Using IAM, you can create and manage AWS users and groups, and use permissions to allow and deny their access to AWS resources.

#### Amazon Inspector

Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS.

#### AWS Certificate Manager

AWS Certificate Manager is a service that lets you easily provision, manage, and deploy Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services.

#### AWS CloudHSM

The AWS CloudHSM service helps you meet corporate, contractual, and regulatory compliance requirements for data security by using dedicated Hardware Security Module (HSM) appliances within the AWS Cloud.

#### AWS Directory Service

AWS Directory Service for Microsoft Active Directory (Enterprise Edition), also known as AWS Microsoft AD, enables your directory-aware workloads and AWS resources to use managed Active Directory in the AWS Cloud.

#### AWS Key Management Service

AWS Key Management Service (KMS) is a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data. 

#### AWS Organizations

AWS Organizations allows you to create groups of AWS accounts that you can use to more easily manage security and automation settings. 

#### AWS Shield

AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that safeguards web applications running on AWS. AWS Shield provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection. There are two tiers of AWS Shield: Standard and Advanced.

#### AWS WAF

AWS WAF is a web application firewall that helps protect your web applications from common web exploits that could affect application availability, compromise security, or consume excessive resources.

### Analytics

#### Amazon Athena

Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to manage, and you pay only for the queries that you run.

#### Amazon EMR

Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable EC2 instances.

#### Amazon CloudSearch

Amazon CloudSearch is a managed service in the AWS Cloud that makes it simple and cost-effective to set up, manage, and scale a search solution for your website or application.

#### Amazon Elasticsearch Service

Amazon Elasticsearch Service makes it easy to deploy, operate, and scale Elasticsearch for log analytics, full text search, application monitoring, and more.

#### Amazon Kinesis

Amazon Kinesis is a platform for streaming data on AWS, offering powerful services to make it easy to load and analyze streaming data, and also providing the ability for you to build custom streaming data applications for specialized needs. Amazon Kinesis currently offers three services: Amazon Kinesis Firehose, Amazon Kinesis Analytics, and Amazon Kinesis Streams.

#### Amazon Kinesis Firehose

Amazon Kinesis Firehose is the easiest way to load streaming data into AWS.

#### Amazon Kinesis Analytics

Amazon Kinesis Analytics is the easiest way to process streaming data in real time with standard SQL without having to learn new programming languages or processing frameworks.

#### Amazon Kinesis Streams

Amazon Kinesis Streams enables you to build custom applications that process or analyze streaming data for specialized needs.

#### Amazon Redshift

Amazon Redshift is a fast, fully managed, petabyte-scale data warehouse that makes it simple and costeffective to analyze all your data using your existing business intelligence tools. 

#### Amazon QuickSight

Amazon QuickSight is a fast, cloud-powered business analytics service that makes it easy to build visualizations, perform ad-hoc analysis, and quickly get business insights from your data.

#### AWS Data Pipeline

AWS Data Pipeline is a web service that helps you reliably process and move data between different AWS compute and storage services, as well as on-premises data sources, at specified intervals.

#### AWS Glue

AWS Glue is a fully managed ETL service that makes it easy to move data between your data stores. AWS Glue guides you through the process of moving your data with an easy-to-use console that helps you understand your data sources, prepare the data for analytics, and load it reliably from data sources to destinations.

### Artificial Intelligence

#### Amazon Lex

Amazon Lex is a service for building conversational interfaces into any application using voice and text.

#### Amazon Polly

Amazon Polly is a service that turns text into lifelike speech.

#### Amazon Rekognition

Amazon Rekognition is a service that makes it easy to add image analysis to your applications.

#### Amazon Machine Learning

Amazon Machine Learning (Amazon ML) is a service that makes it easy for developers of all skill levels to use machine learning technology.

### Mobile Services

#### AWS Mobile Hub

AWS Mobile Hub provides an integrated console experience that you can use to quickly create and configure powerful mobile app backend features and integrate them into your mobile app.

#### Amazon Cognito

Amazon Cognito lets you easily add user sign-up and sign-in to your mobile and web apps.

#### Amazon Pinpoint

Amazon Pinpoint makes it easy to run targeted campaigns to drive user engagement in mobile apps.

#### AWS Device Farm

AWS Device Farm is an app testing service that lets you test and interact with your Android, iOS, and web apps on many devices at once, or reproduce issues on a device in real time.

#### AWS Mobile SDK

The AWS Mobile SDK helps you build high quality mobile apps quickly and easily. 

#### Amazon Mobile Analytics

With Amazon Mobile Analytics, you can measure app usage and app revenue.

### Application Services

#### AWS Step Functions

AWS Step Functions makes it easy to coordinate the components of distributed applications and microservices using visual workflows.

#### Amazon API Gateway

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

#### Amazon Elastic Transcoder

Amazon Elastic Transcoder is media transcoding in the cloud. 

#### Amazon SWF

Amazon Simple Workflow (Amazon SWF) helps developers build, run, and scale background jobs that have parallel or sequential steps.

### Messaging

#### Amazon SQS

Amazon Simple Queue Service (Amazon SQS) is a fast, reliable, scalable, fully managed message queuing service.

#### Amazon SNS

Amazon Simple Notification Service (Amazon SNS) is a fast, flexible, fully managed push notification service that lets you send individual messages or to fan-out messages to large numbers of recipients.

#### Amazon SES

Amazon Simple Email Service (Amazon SES) is a cost-effective email service built on the reliable and scalable infrastructure that Amazon.com developed to serve its own customer base.

