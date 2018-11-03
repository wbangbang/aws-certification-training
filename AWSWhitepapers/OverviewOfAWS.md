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