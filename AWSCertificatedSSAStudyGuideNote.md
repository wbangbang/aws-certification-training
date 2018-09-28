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

A subnet is a segment of an Amazon VPC’s IP address range where you can launch Amazon EC2 instances, Amazon Relational Database Service (Amazon RDS) databases, and other AWS resources. AWS reserves the first four IP addresses and the last IP address of every subnet for internal networking purposes.

After creating an Amazon VPC, you can add one or more subnets in each Availability Zone. Subnets reside within one Availability Zone and cannot span zones. 

Subnets can be classified as public, private, or VPN-only. Regardless of the type of subnet, the internal IP
address range of the subnet is always private (that is, non-routable on the Internet).

### Route Tables

A route table is a logical construct within an Amazon VPC that contains a set of rules (called routes) that are applied to the subnet and used to determine where network traffic is directed. A route table’s routes are what permit Amazon EC2 instances within different subnets within an Amazon VPC to communicate with each other.

You should remember the following points about route tables:

* Your VPC has an implicit router.
* Your VPC automatically comes with a main route table that you can modify.
* You can create additional custom route tables for your VPC.
* Each subnet must be associated with a route table, which controls the routing for the subnet. If you don’t explicitly associate a subnet with a particular route table, the subnet uses the main route table.
* You can replace the main route table with a custom table that you’ve created so that each new subnet is automatically associated with it.
* Each route in a table specifies a destination CIDR and a target; for example, traffic destined for 172.16.0.0/12 is targeted for the VPG. AWS uses the most specific route that matches the traffic to determine how to route the traffic.

### Internet Gateways

An IGW provides a target in your Amazon VPC route tables for Internet-routable traffic, and it performs network address translation for instances that have been assigned public IP addresses.

You must do the following to create a public subnet with Internet access:

* Attach an IGW to your Amazon VPC.
* Create a subnet route table rule to send all non-local traffic (0.0.0.0/0) to the IGW.
* Configure your network ACLs and security group rules to allow relevant traffic to flow to and from your instance.

You must do the following to enable an Amazon EC2 instance to send and receive traffic from the Internet:

* Assign a public IP address or EIP address.

Follwing is showing VPC, subnet, route table, and an Internet gateway:
![VPC, subnet, route table, and an Internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/images/internet-gateway-overview-diagram.png)

### Dynamic Host Configuration Protocol (DHCP) Option Sets

AWS automatically creates and associates a DHCP option set for your Amazon VPC upon creation and sets two options: domain-name-servers (defaulted to AmazonProvidedDNS) and domain-name (defaulted to the domain name for your region). 

The DHCP option sets element of an Amazon VPC allows you to direct Amazon EC2 host name assignments to your own resources. 

Every Amazon VPC must have only one DHCP option set assigned to it

### Elastic IP Addresses (EIPs)

An Elastic IP Addresses (EIP) is a static, public IP address in the pool for the region that you can allocate to your account (pull from the pool) and release (return to the pool). 

Important points for the exam:

* You must first allocate an EIP for use within a VPC and then assign it to an instance.
* EIPs are specific to a region (that is, an EIP in one region cannot be assigned to an instance within an Amazon VPC in a different region).
* There is a one-to-one relationship between network interfaces and EIPs.
* You can move EIPs from one instance to another, either in the same Amazon VPC or a different Amazon VPC within the same region.
* EIPs remain associated with your AWS account until you explicitly release them.
* There are charges for EIPs allocated to your account, even when they are not associated with a resource.

### Elastic Network Interfaces (ENIs)

An Elastic Network Interface (ENI) is a virtual network interface that you can attach to an instance in an Amazon VPC. ENIs are only available within an Amazon VPC, and they are associated with a subnet upon creation.

### Endpoints

An Amazon VPC endpoint enables you to create a private connection between your Amazon VPC and another AWS service without requiring access over the Internet or through a NAT instance, VPN connection, or AWS Direct Connect.

You must do the following to create an Amazon VPC endpoint:

* Specify the Amazon VPC.
* Specify the service. A service is identified by a prefix list of the form com.amazonaws.\<region\>.\<service\>.
* Specify the policy. You can allow full access or create a custom policy. This policy can be changed at any time.
* Specify the route tables. A route will be added to each specified route table, which will
state the service as the destination and the endpoint as the target.

### Peering

An Amazon VPC peering connection is a networking connection between two Amazon VPCs. You can create an Amazon VPC peering connection between your own Amazon VPCs or with an Amazon VPC in another AWS account within a single region. A peering connection is neither a gateway nor an Amazon VPN connection and does not introduce a single point of failure for communication.

Peering connections are created through a request/accept protocol. 

Important points for the exam:

* You cannot create a peering connection between Amazon VPCs that have matching or overlapping CIDR blocks.
* You cannot create a peering connection between Amazon VPCs in different regions.
* Amazon VPC peering connections do not support transitive routing.
* You cannot have more than one peering connection between the same two Amazon VPCs at the same time.

### Security Groups

A security group is a virtual **stateful** firewall that controls inbound and outbound network traffic to AWS resources and Amazon EC2 instances. 

Important points for the exam:

* You can create up to 500 security groups for each Amazon VPC.
* You can add up to 50 inbound and 50 outbound rules to each security group. If you need to apply more than 100 rules to an instance, you can associate up to five security groups with each network interface.
* You can specify allow rules, but not deny rules. This is an important difference between security groups and ACLs.
* You can specify separate rules for inbound and outbound traffic.
* By default, no inbound traffic is allowed until you add inbound rules to the security group.
* By default, new security groups have an outbound rule that allows all outbound traffic.
* You can remove the rule and add outbound rules that allow specific outbound traffic only.
* Security groups are stateful. This means that responses to allowed inbound traffic are allowed to flow outbound regardless of outbound rules and vice versa. This is an important difference between security groups and network ACLs.
* Instances associated with the same security group can’t talk to each other unless you add rules allowing it (with the exception being the default security group). 
* You can change the security groups with which an instance is associated after launch, and the changes will take effect immediately.

### Network Access Control Lists (ACLs)

A network access control list (ACL) is another layer of security that acts as a **stateless** firewall on a subnet level. 

Amazon VPCs are created with a modifiable default network ACL associated with every subnet that allows all inbound and outbound traffic. When you create a custom network ACL, its initial configuration will deny all inbound and outbound traffic until you create rules that allow otherwise. 

Overall, every subnet must be associated with a network ACL.

Comparison of Security Groups and Network ACLs:

| Security Group | Network ACL |
| :------------- | :---------- |
| Operates at the instance level (first layer of defense) | Operates at the subnet level (second layer of defense) |
| Supports allow rules only | Supports allow rules and deny rules |
| Stateful: Return traffic is automatically allowed, regardless of any rules | Stateless: Return traffic must be explicitly allowed by rules |
| AWS evaluates all rules before deciding whether to allow traffic | AWS processes rules in number order when deciding whether to allow traffic |
| Applied selectively to individual instances | Automatically applied to all instances in the associated subnets; this is a backup layer of defense, so you don’t have to rely on someone specifying the security group |

### Network Address Translation (NAT) Instances and NAT Gateways

#### NAT Instance

To allow instances within a private subnet to access Internet resources through the IGW via a NAT instance, you must do the following:

* Create a security group for the NAT with outbound rules that specify the needed Internet resources by port, protocol, and IP address.
* Launch an Amazon Linux NAT AMI as an instance in a public subnet and associate it with the NAT security group.
* Disable the Source/Destination Check attribute of the NAT.
* Configure the route table associated with a private subnet to direct Internet-bound traffic to the NAT instance (for example, i-1a2b3c4d).
* Allocate an EIP and associate it with the NAT instance.

#### NAT Gateway

To allow instances within a private subnet to access Internet resources through the IGW via a NAT gateway, you must do the following:

* Configure the route table associated with the private subnet to direct Internet-bound traffic to the NAT gateway (for example, nat-1a2b3c4d).
* Allocate an EIP and associate it with the NAT gateway.

### Virtual Private Gateways (VPGs), Customer Gateways (CGWs), and Virtual Private Networks (VPNs)

![VPC with VPN connection to a customer network](https://docs.aws.amazon.com/vpc/latest/userguide/images/VPN_Basic_Diagram.png)

Important points for the exam:

* The VPG is the AWS end of the VPN tunnel.
* The CGW is a hardware or software application on the customer’s side of the VPN tunnel.
* You must initiate the VPN tunnel from the CGW to the VPG.
* VPGs support both dynamic routing with BGP and static routing.
* The VPN connection consists of two tunnels for higher availability to the VPC.

### Exam Essentials

* Understand what a VPC is and its core and optional components.
* Understand the purpose of a subnet.
* Identify the difference between a public subnet, a private subnet, and a VPN-Only subnet.
* Understand the purpose of a route table.
* Understand the purpose of an IGW. 
* Understand what DHCP option sets provide to an Amazon VPC.
* Know the difference between an Amazon VPC public IP address and an EIP address.
* Understand what endpoints provide to an Amazon VPC.
* Understand Amazon VPC peering.
* Know the difference between a security group and a network ACL
* Understand what a NAT provides to an Amazon VPC. 
* Understand the components needed to establish a VPN connection from a network to an Amazon VPC. 



<span id="chapter-5"></span>
## Chapter 5 - Elastic Load Balancing, Amazon CloudWatch, and Auto Scaling

### Elastic Load Balancing

> Tip: Elastic Load Balancing is a highly available service itself and can be used to help build highly available architectures.

#### Types of Load Balancers

##### Internet-Facing Load Balancers

> Tip: An AWS recommended best practice is always to reference a load balancer by its DNS name, instead of by the IP address of the load balancer, in order to provide a single, stable entry point.

##### Internal Load Balancers

##### HTTPS Load Balancers

#### Listeners

Every load balancer must have one or more listeners configured.

Every listener is configured with a protocol and a port (client to load balancer) for a front-end connection and a protocol and a port for the back-end (load balancer to Amazon EC2 instance) connection. 

Elastic Load Balancing supports the following protocols:

* HTTP
* HTTPS
* TCP
* SSL

#### Configuring Elastic Load Balancing

##### Idle Connection Timeout

##### Cross-Zone Load Balancing

##### Connection Draining

##### Proxy Protocol

##### Sticky Sessions

##### Health Checks

### Amazon CloudWatch

### Auto Scaling

#### Auto Scaling Plans

##### Maintain Current Instance Levels

> Tip: Steady state workloads that need a consistent number of Amazon EC2 instances at all times can use Auto Scaling to monitor and keep that specific number of Amazon EC2 instances running.

##### Manual Scaling

> Tip: Manual scaling out can be very useful to increase resources for an infrequent event, such as the release of a new game version that will be available for download and require a user registration. For extremely large-scale events, even the Elastic Load Balancing load balancers can be pre-warmed by working with your local solutions architect or AWS Support.

##### Scheduled Scaling

> Tip: Recurring events such as end-of-month, quarter, or year processing, or scheduled and recurring automated load and performance testing, can be anticipated and Auto Scaling can be ramped up appropriately at the time of the scheduled event.

##### Dynamic Scaling

#### Auto Scaling Components

##### Launch Configuration

The default limit for launch configurations is 100 per region.

Auto Scaling may cause you to reach limits of other services, such as the default number of Amazon EC2 instances you can currently launch within a region, which is **20**.

##### Auto Scaling Group

An Auto Scaling group can use either On-Demand or Spot Instances as the Amazon EC2 instances it manages.

> Tip: Auto Scaling supports using cost-effective Spot Instances. This can be very useful when you are hosting sites where you want to provide additional compute capacity but are price constrained. 

##### Scaling Policy

> Tip: Scale out quickly; scale in slowly.

### Exam Essentials

* Understand what the Elastic Load Balancing service provides.
* Know the types of load balancers the Elastic Load Balancing service provides and when to use each one.
* Know the types of listeners the Elastic Load Balancing service provides and the use case and requirements for using each one. 
* Understand the configuration options for Elastic Load Balancing. 
* Know what an Elastic Load Balancing health check is and why it is important.
* Understand what the amazon CloudWatch service provides and what use cases there are for using it.
* Know the differences between the two types of monitoring—basic and detailed—for Amazon CloudWatch.
* Understand Auto Scaling and why it is an important advantage of the AWS Cloud.
* Know when and why to use Auto Scaling.
* Know the supported Auto Scaling plans. 
* Understand how to build an Auto Scaling launch configuration and an Auto Scaling group and what each is used for. 
* Know what a scaling policy is and what use cases to use it for.
* Understand how Elastic Load Balancing, amazon CloudWatch, and Auto Scaling are used together to provide dynamic scaling.



<span id="chapter-6"></span>
## Chapter 6 - AWS Identity and Access Management (IAM)

### Introduction

IAM is not:

* IAM is not an identity store/authorization system for your applications.
* IAM is not operating system identity management.

| Use Case                | Technology Solutions                                                |
| :---------------------- | :------------------------------------------------------------------ |
| Operating System Access | Active Directory LDAP Machine-specific accounts                     |
| Application Access      | Active Directory Or Application User Repositories Or Amazon Cognito |
| AWS Resources           | IAM                                                                 |

### Principals

A principal is an IAM entity that is allowed to interact with AWS resources. There are three types of principals: root users, IAM users, and roles/temporary security tokens.

#### Root User

#### IAM Users

#### Roles/Temporary Security Tokens

Use cases:

* Amazon EC2 Roles
* Cross-Account Access
* Federation

> Tip: Using IAM roles for Amazon EC2 removes the need to store AWS credentials in a configuration file.

| Principal                       | Traits                                                                     |
| :------------------------------ | :------------------------------------------------------------------------- |
| Root User                       | Cannot be limited Permanent                                                |
| IAM Users                       | Access controlled by policy; Durable; Can be removed by IAM administrator  | 
| Roles/Temporary Security Tokens | Access controlled by policy Temporary; Expire after specific time interval |

### Authentication

3 ways to authenticates principals:

* User Name/Password
* Access Key
* Access Key/Session Token

### Authorization

Authorization is handled in IAM by defining specific privileges in policies and associating those policies with principals.

#### Policies

Policy documents contain one or more permissions, with each permission defining:

* Effect - Allow or Deny
* Service
* Resource - ARN: ```"arn:aws:service:region:account-id:[resourcetype:]resource"```
* Action
* Condition