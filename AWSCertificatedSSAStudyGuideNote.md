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

#### Associating Policies with Principals

### Other Key Features

#### Multi-Factor Authentication (MFA)

> Tip: MFA requires you to verify your identity with both something you know and something you have.

#### Rotating Keys

#### Resolving Multiple Permissions

It is important to know how conflicts between these permissions are resolved:

1. Initially the request is denied by default.
2. All the appropriate policies are evaluated; if there is an explicit “deny” found in any policy, the request is denied and evaluation stops.
3. If no explicit “deny” is found and an explicit “allow” is found in any policy, the request is allowed.
4. If there are no explicit “allow” or “deny” permissions found, then the default “deny” is maintained and the request is denied. 

### Exam Essentials

* Know the different principals in IAM.
* Know how principals are authenticated in IAM.
* Know the parts of a policy.
* Know how a policy is associated with a principal.
* Understand MFA.
* Understand key rotation.
* Understand IAM roles and federation.
* Know how to resolve conflicting permissions. 



<span id="chapter-7"></span>
## Chapter 7 - Databases and AWS

### Database Primer

### Amazon Relational Database Service (Amazon RDS)

#### Database (DB) Instances

The Amazon RDS service itself provides an Application Programming Interface (API) that lets you create and manage one or more DB Instances. A DB Instance is an isolated database environment deployed in your private network segments in the cloud.

The compute and memory resources of a DB Instance are determined by its DB Instance class.

Many features and common configuration settings are exposed and managed using DB parameter groups and DB option groups.

A DB parameter group acts as a container for engine configuration values that can be applied to one or more DB Instances.

A DB option group acts as a container for engine features, which is empty by default.

#### Operational Benefits

| Responsibility       | Database OnPremise | Database on Amazon EC2 | Database on Amazon RDS |
| :------------------- | :----------------- | :--------------------- | :--------------------- |
| App Optimization     | You                | You                    | You                    |
| Scaling              | You                | You                    | AWS                    |
| High Availability    | You                | You                    | AWS                    |
| Backups              | You                | You                    | AWS                    |
| DB Engine Patches    | You                | You                    | AWS                    |
| Software Installation| You                | You                    | AWS                    |
| OS Patches           | You                | You                    | AWS                    |
| OS Installation      | You                | AWS                    | AWS                    |
| Server Maintenance   | You                | AWS                    | AWS                    |
| Rack and Stack       | You                | AWS                    | AWS                    |
| Power and Cooling    | You                | AWS                    | AWS                    |

#### Database Engines

#### Storage Options

Amazon RDS is built using Amazon Elastic Block Store (Amazon EBS) and allows you to select the right storage option based on your performance and cost requirements. 

| Type        | Magnetic | General Purpose (SSD) | Provisioned IOPS (SSD) |
| :---------- | :------- | :-------------------- | :--------------------- |
| Size        | +++      | +++++                 | +++++                  |
| Performance | +        | +++                   | +++++                  |
| Cost        | ++       | +++                   | +++++                  |

#### Backup and Recovery

* Recovery Point Objective (RPO) - defined as the maximum period of data loss that is acceptable in the event of a failure or incident. 
* Recovery Time Objective (RTO) - defined as the maximum amount of downtime that is permitted to recover from backup and to resume processing. 

##### Automated Backups

One day of backups will be retained by default, but you can modify the retention period up to a maximum of 35 days. When you delete a DB Instance, all automated backup snapshots are deleted and cannot be recovered. Manual snapshots, however, are not deleted.

##### Manual DB Snapshots

> Tip: For busy databases, use Multi-AZ to minimize the performance impact of a snapshot. During the backup window, storage I/O may be suspended while your data is being backed up, and you may experience elevated latency. This I/O suspension typically lasts for the duration of the snapshot. This period of I/O suspension is shorter for Multi-AZ DB deployments because the backup is taken from the standby, but latency can occur during the backup process.

##### Recovery

You cannot restore from a DB snapshot to an existing DB Instance; a new DB Instance is created when you restore.

#### High Availability with Multi-AZ

Multi-AZ allows you to place a secondary copy of your database in another Availability Zone for disaster recovery purposes. 

Amazon RDS automatically replicates the data from the master database or primary instance to the slave database or secondary instance using synchronous replication.

> Tip: It is important to remember that Multi-AZ deployments are for disaster recovery only; they are not meant to enhance database performance. The standby DB Instance is not available to offline queries from the primary master DB Instance. To improve database performance using multiple DB Instances, use read replicas or other DB caching technologies such as Amazon ElastiCache.

#### Scaling Up and Out

##### Vertical Scalability

##### Horizontal Scalability with Partitioning

Partitioning, or sharding, allows you to scale horizontally to handle more users and requests but requires additional logic in the application layer.

##### Horizontal Scalability with Read Replicas

Some common scenarios include:

* Scale beyond the capacity of a single DB Instance for read-heavy workloads. 
* Handle read traffic while the source DB Instance is unavailable. For example, due to I/O suspension for backups or scheduled maintenance, you can direct read traffic to a replica.
* Offload reporting or data warehousing scenarios against a replica instead of the primary DB Instance.

> Tip; You can create one or more replicas of a database within a single AWS Region or across multiple AWS Regions. To enhance your disaster recovery capabilities or reduce global latencies, you can use cross-region read replicas to serve read traffic from a region closest to your global users or migrate your databases across AWS Regions. 

#### Security

### Amazon Redshift

#### Clusters and Nodes

A cluster is composed of a leader node and one or more compute nodes. The client application interacts directly only with the leader node, and the compute nodes are transparent to external applications.

![Amazon Redshift cluster architecture](https://docs.aws.amazon.com/redshift/latest/dg/images/02-NodeRelationships.png)

Amazon Redshift currently has support for six different node types and each has a different mix of CPU, memory, and storage. The six node types are grouped into two categories: **Dense Compute** and **Dense Storage**. 

The Dense Compute node types support clusters up to 326TB using fast SSDs, while the Dense Storage nodes support clusters up to 2PB using large magnetic disks. 

Amazon Redshift allows you to resize a cluster to add storage and compute capacity over time. During a resize operation, the database will become read-only until the operation is finished.as your needs evolve.

#### Table Design

##### Data Types

##### Compression Encoding

###### Distribution Strategy

* EVEN distribution
* KEY distribution
* ALL distribution

##### Sort Keys

#### Loading Data

> Tip: A COPY command can load data into a table in the most efficient manner, and it supports multiple types of input data sources. The fastest way to load data into Amazon Redshift is doing bulk data loads from flat files stored in an Amazon Simple Storage Service (Amazon S3) bucket or from an Amazon DynamoDB table.

#### Querying Data

#### Snapshots

#### Security

### Amazon DynamoDB

To help maintain consistent, fast performance levels, all table data is stored on high-performance SSD disk drives.

#### Data Model

The basic components of the Amazon DynamoDB data model include tables, items, and attributes.

Individual items in an Amazon DynamoDB table can have any number of attributes, although there is a limit of 400KB on the item size.

Each attribute in an item is a name/value pair. An attribute can be a single-valued or multivalued **set**.

##### Data Types

Data types fall into three major categories: Scalar, Set, or Document.

Amazon DynamoDB supports the following five scalar types:

* String
* Number
* Binary
* Boolean
* Null

Each value in a set needs to be unique and must be the same data type. Amazon DynamoDB supports three set types: 

* String Set
* Number Set
* Binary Set

Amazon DynamoDB supports two document types:

* List
* Map

##### Primary Key

When you create a table, you must specify the primary key of the table in addition to the table name.

Amazon DynamoDB supports two types of primary keys, and this configuration cannot be changed after a table has been created:

* Partition Key
* Partition and Sort Key

Furthermore, each primary key attribute must be defined as type string, number, or binary.

> Tip: If you are performing many reads or writes per second on the same primary key, you will not be able to fully use the compute capacity of the Amazon DynamoDB cluster. A best practice is to maximize your throughput by distributing requests across the full range of partition keys.

##### Provisioned Capacity

Each operation against an Amazon DynamoDB table will consume some of the provisioned capacity units. The specific amount of capacity units consumed depends largely on the size of the item, but also on other factors. 

##### Secondary Indexes

When you create a table with a partition and sort key, you can optionally define one or more secondary indexes on that table.

Amazon DynamoDB supports two different kinds of indexes:

* Global Secondary Index
* Local Secondary Index

While a table can only have one local secondary index, you can have multiple global secondary indexes.

#### Writing and Reading Data

##### Writing Items

##### Reading Items

By default, a GetItem operation performs an eventually consistent read.

##### Eventual Consistency

##### Batch Operations

##### Searching Items

Amazon DynamoDB gives you two operations, Query and Scan.

> Tip: For most operations, performing a Query operation instead of a Scan operation will be the most efficient option. Performing a Scan operation will result in a full scan of the entire table or secondary index, then it filters out values to provide the desired result. Use a Query operation when possible and avoid a Scan on a large table or index for only a small number of items.

#### Scaling and Partitioning

One single partition can hold about 10GB of data and supports a maximum of 3,000 read capacity units or 1,000 write capacity units.

Additional partitions can be added by splitting an existing partition. After a partition is split, however, it cannot be merged back together. 

> Tip: To maximize Amazon DynamoDB throughput, create tables with a partition key that has a large number of distinct values and ensure that the values are requested fairly uniformly. Adding a random element that can be calculated or hashed is one common technique to improve partition distribution.

#### Security

#### Amazon DynamoDB Streams

### Exam Essentials

* Know what a relational database is.
* Understand which databases are supported by Amazon RDS.
* Understand the operational benefits of using Amazon RDS.
* Remember that you cannot access the underlying OS for Amazon RDS DB instances.
* Know that you can increase availability using Amazon RDS Multi-AZ deployment.
* Understand the importance of RPO and RTO.
* Understand that Amazon RDS handles Multi-AZ failover for you. 
* Remember that Amazon RDS read replicas are used for scaling out and increased performance. 
* Know what a NoSQL database is.
* Remember that Amazon DynamoDB is AWS NoSQL service.
* Know what a data warehouse is.
* Remember that Amazon Redshift is AWS data warehouse service.



<span id="chapter-8"></span>
## Chapter 8 - SQS, SWF, and SNS

### Amazon Simple Queue Service (Amazon SQS)

An Amazon SQS queue is basically a buffer between the application components that receive data and those components that process the data in your system. 

#### Message Lifecycle

#### Delay Queues and Visibility Timeouts

![Diagram of visibility time out](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/images/sqs-visibility-timeout-diagram.png)

Amazon SQS supports up to 12 hours’ maximum visibility timeout.


#### Queue Operations, Unique IDs, and Metadata

#### Queue and Message Identifiers

Amazon SQS uses three identifiers that you need to be familiar with: queue URLs, message IDs, and receipt handles.

Your messages are identified via a globally unique ID that Amazon SQS returns when the message is delivered to the queue. 

Each time you receive a message from a queue, you receive a receipt handle for that message. The handle is associated with the act of receiving the message, not with the message itself.

#### Message Attributes

Message attributes allow you to provide structured metadata items (such as timestamps, geospatial data, signatures, and identifiers) about the message. 

#### Long Polling

With long polling, you send a WaitTimeSeconds argument to ReceiveMessage of up to 20 seconds. 

#### Dead Letter Queues

A dead letter queue is a queue that other (source) queues can target to send messages that for some reason could not be successfully processed. A primary benefit of using a dead letter queue is the ability to sideline and isolate the unsuccessfully processed messages.

#### Access Control

Amazon SQS Access Control allows you to assign policies to queues that grant specific interactions to other accounts without that account having to assume IAM roles from your account. These policies are written in the same JSON language as IAM. 

### Amazon Simple Workflow Service (Amazon SWF)

#### Workflows

Using Amazon SWF, you can implement distributed, asynchronous applications as workflows.

##### Workflow Domains

You must specify a domain for all the components of a workflow, such as the workflow type and activity types. Workflows in different domains cannot interact with one another.

##### Workflow History

#### Actors

Actors can be workflow starters, deciders, or activity workers. These actors communicate with Amazon SWF through its API.

#### Tasks

Three types of tasks: activity tasks, AWS Lambda tasks, and decision tasks.

#### Task Lists

#### Long Polling

#### Object Identifiers

#### Workflow Execution Closure

#### Lifecycle of a Workflow Execution

### Amazon Simple Notification Service (Amazon SNS)

Amazon SNS follows the publish-subscribe (pub-sub) messaging paradigm, with notifications being delivered to clients using a push mechanism that eliminates the need to check periodically (or poll) for new information and updates.

Amazon SNS consists of two types of clients: publishers and subscribers (sometimes known as producers and consumers). 

![Diagram of topic delivery](https://docs.aws.amazon.com/sns/latest/dg/images/sns-how-works.png)

#### Common Amazon SNS Scenarios

##### Fanout

This allows for parallel asynchronous processing. 

![Diagram of fanout scenario](https://docs.aws.amazon.com/sns/latest/dg/images/sns-fanout.png)

##### Application and System Alerts

##### Push Email and Text Messaging

##### Mobile Push Notifications

### Exam Essentials

* Know how to use Amazon SQS.
* Understand Amazon SQS visibility timeouts.
* Know how to use Amazon SQS long polling. 
* Know how to use Amazon SWF.
* Know the basics of an Amazon SWF workflow.
* Understand the different Amazon SWF actors.
* Understand Amazon SNS basics.
* Know the different protocols used with Amazon SNS.



<span id="chapter-9"></span>
## Chapter 9 - Domain Name System (DNS) and Amazon Route 53

### Domain Name System (DNS)

DNS is a globally-distributed service that is foundational to the way people use the Internet. DNS uses a hierarchical name structure, and different levels in the hierarchy are each separated with a dot (.). 

#### Domain Name System (DNS) Concepts

##### Top-Level Domains (TLDs)

Each domain name becomes registered in a central database, known as the WhoIS database.

##### Domain Names

##### IP Addresses

##### Hosts

##### Subdomains

The difference between a host name and a subdomain is that a host defines a computer or resource, while a subdomain extends the parent domain. 

##### Fully Qualified Domain Name (FQDN)

##### Name Servers

A name server is a computer designated to translate domain names into IP addresses.

##### Zone Files

A zone file is a simple text file that contains the mappings between domain names and IP addresses.

Zone files reside in name servers and generally define the resources available under a specific domain, or the place where one can go to get that information.

##### Top-Level Domain (TLD) Name Registrars

A domain name registrar is an organization or commercial entity that manages the reservation of Internet domain names. 

#### Steps Involved in Domain Name System (DNS) Resolution

Root Server -> Top-Level Domain (TLD) Servers -> Domain-Level Name Servers

In almost all cases, the requester will be what is called a **resolving name server**, which is a server that is configured to ask other servers questions. Its primary function is to act as an intermediary for a user, caching previous query results to improve speed and providing the addresses of appropriate root servers to resolve new requests.

#### Record Types

Each zone file contains records. In its simplest form, a record is a single mapping between a resource and a name.

##### Start of Authority (SOA) Record

A Start of Authority (SOA) record is mandatory in all zone files, and it identifies the base DNS information about the domain. Each zone contains a single SOA record.

##### A and AAAA

##### Canonical Name (CNAME)

##### Mail Exchange (MX)

##### Name Server (NS)

##### Pointer (PTR)

##### Sender Policy Framework (SPF)

##### Text (TXT)

##### Service (SRV)

### Amazon Route 53 Overview

Amazon Route 53 performs three main functions:

* Domain registration
* DNS service
* Health checking

#### Domain Registration

#### Domain Name System (DNS) Service

#### Hosted Zones

* private
* public

> Tip: You can use Amazon S3 to host your static website at the hosted zone (for example, domain.com) and redirect all requests to a subdomain (for example, www.domain.com). Then, in Amazon Route 53, you can create an alias resource record that sends requests for the root domain to the Amazon S3 bucket.

> Tip: Use an alias record, not a CNAME, for your hosted zone. CNAMEs are not allowed for hosted zones in Amazon Route 53.

> Tip: Do not use A records for subdomains (for example, www.domain.com), as they refer to hardcoded IP addresses. Instead, use Amazon Route 53 alias records or traditional CNAME records to always point to the right resource, wherever your site is hosted, even when the physical server has changed its IP address.

#### Supported Record Types

When you create a resource record set, you choose a routing policy, which determines how Amazon Route 53 responds to queries. Routing policy options are simple, weighted, latencybased, failover, and geolocation.  

#### Amazon Route 53 Enables Resiliency

### Exam Essentials

* Understand what DNS is.
* Know how DNS registration works.
* Remember the steps involved in DNS resolution.
* Remember the different record types.
* Remember the different routing policies.



<span id="chapter-10"></span>
## Chapter 10 - Amazon ElastiCache

### In-Memory Caching

Memcached is a simple-to-use in-memory key/value store that can be used to store arbitrary types of data. It is one of the most popular cache engines. Redis is a flexible in-memory data structure store that can be used as a cache, database, or even as a message broker. Amazon ElastiCache allows developers to easily deploy and manage cache environments running either Memcached or Redis.

### Amazon ElastiCache

#### Data Access Patterns

You should evaluate the access pattern of the data before you decide to store it in cache. 

#### Cache Engines

#### Nodes and Clusters

#### Memcached Auto Discovery

For Memcached clusters partitioned across multiple nodes, Amazon ElastiCache supports Auto Discovery with the provided client library.

#### Scaling

##### Horizontal Scaling

With Memcached, you can partition your data and scale horizontally to 20 nodes or more. With Auto Discovery, your application can discover Memcached nodes that are added or removed from a cluster.

A Redis cluster consists of a single cache node that is handling read and write transactions. Additional clusters can be created and grouped into a Redis replication group.

##### Vertical Scaling

You can quickly spin up a new cluster with the desired cache node types and start redirecting traffic to the
new cluster. It’s important to understand that a new Memcached cluster always starts empty, while a Redis cluster can be initialized from a backup.

#### Replication and Multi-AZ

Cache clusters running Redis support the concept of replication groups. A replication group consists of up to six clusters, with five of them designated as read replicas. 

##### Multi-AZ Replication Groups

It’s important to keep in mind that replication between the clusters is performed asynchronously and there will be a small delay before data is available on all cluster nodes.

#### Backup and Recovery

Snapshots cannot be created for clusters using the Memcached engine because it is a purely in-memory key/value store and always starts empty. 

Snapshots require compute and memory resources to perform and can potentially have a performance impact on heavily used clusters. 

#### Access Control

### Exam Essentials

* Know how to use Amazon ElastiCache.
* Understand when to use a specific cache engine.
* Understand how to scale a Redis cluster horizontally. 
* Understand how to scale a Memcached cluster horizontally.
* Know how to back up your Amazon ElastiCache cluster.



<span id="chapter-11"></span>
## Chapter 11 - Additional Key Services

### Storage and Content Delivery

#### Amazon CloudFront

Amazon CloudFront is a global Content Delivery Network (CDN) service.

##### Overview

CDNs use Domain Name System (DNS) geo-location to determine the geographic location of each request for a web page or other content, then they serve that content from edge caching servers closest to that location
instead of the original web server.

Amazon CloudFront supports all content that can be served over HTTP or HTTPS.

##### Amazon CloudFront Basics

**Distributions** To use Amazon CloudFront, you start by creating a distribution, which is
identified by a DNS domain name such as d111111abcdef8.cloudfront.net. 

**Origins** When you create a distribution, you must specify the DNS domain name of the origin, from which you want Amazon CloudFront to get the definitive version of your objects (web files). 

**Cache Control** Once requested and served from an edge location, objects stay in the cache until they expire or are evicted to make room for more frequently requested content. By default, objects expire from the cache after 24 hours.

Optionally, you can control how long objects stay in an Amazon CloudFront cache before expiring - you can choose to use Cache-Control headers set by your origin server or you can set the minimum, maximum, and default Time to Live (TTL) for objects in your Amazon CloudFront distribution.

You can also remove copies of an object from all Amazon CloudFront edge locations at any time by calling the invalidation Application Program Interface (API).

Instead of invalidating objects manually or programmatically, it is a best practice to use a version identifier as part of the object (file) path name.

##### Amazon CloudFront Advanced Features

**Dynamic Content, Multiple Origins, and Cache Behaviors** 

A cache behavior lets you configure a variety of Amazon CloudFront functionalities for a given URL path pattern for files on your website. 

Cache behaviors are applied in order; if a request does not match the first path pattern, it drops down to the next path pattern. 

**Private Content**

Amazon CloudFront provides several mechanisms to allow you to serve private content. These include:

* Signed URLs
* Signed Cookies
* Origin Access Identities (OAI)

##### Use Cases

There are several use cases where Amazon CloudFront is an excellent choice, including, but not limited to:

* Serving the Static Assets of Popular Websites 
* Serving a Whole Website or Web Application
* Serving Content to Users Who Are Widely Distributed Geographically 
* Distributing Software or Other Large Files
* Serving Streaming Media

There are also use cases where CloudFront is not appropriate, including:

* All or Most Requests Come From a Single Location
* All or Most Requests Come Through a Corporate VPN

#### AWS Storage Gateway

AWS Storage Gateway is a service connecting an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organization’s onpremises IT environment and AWS storage infrastructure.

##### Overview

There are three configurations for AWS Storage Gateway:

**Gateway-Cached Volumes**
All data stored on a Gateway-Cached volume is moved to Amazon S3, while recently read data is retained in local storage to provide low-latency access. While each volume is limited to a maximum size of 32TB, a single gateway can support up to 32 volumes for a maximum storage of 1 PB.

All Gateway-Cached volume data and snapshot data is transferred to Amazon S3 over encrypted Secure Sockets Layer (SSL) connections. It is encrypted at rest in Amazon S3 using Server-Side Encryption (SSE).

**Gateway-Stored Volumes**
Gateway-Stored volumes allow you to store your data on your on-premises storage and asynchronously back up that data to Amazon S3. The data is backed up in the form of Amazon Elastic Block Store (Amazon EBS) snapshots. While each volume is limited to a maximum size of 16TB, a single gateway can support up to 32 volumes for a maximum storage of 512TB.

**Gateway Virtual Tape Libraries (VTL)**
The VTL interface lets you leverage your existing tape-based backup application infrastructure to store data on virtual tape cartridges that you create on your Gateway-VTL.

A gateway can contain up to 1,500 tapes (1 PB) of total tape data. 

When your tape software ejects a tape, it is archived on a Virtual Tape Shelf (VTS) and stored in Amazon Glacier.

##### Use Cases

* Gateway-Cached volumes enable you to expand local storage hardware to Amazon S3, allowing you to store much more data without drastically increasing your storage hardware or changing your storage processes.
* Gateway-Stored volumes provide seamless, asynchronous, and secure backup of your onpremises storage without new processes or hardware.
* Gateway-VTLs enable you to keep your current tape backup software and processes while storing your data more cost-effectively and simply on the cloud.

### Security

#### AWS Directory Service

AWS Directory Service is a managed service offering that provides directories that contain information about your organization, including users, groups, computers, and other resources.

##### Overview

Three directory types:

* AWS Directory Service for Microsoft Active Directory (Enterprise Edition)
* Simple AD
* AD Connector

##### Use Cases

* AWS Directory Service for Microsoft Active Directory (Enterprise Edition) is your best choice if you have more than 5,000 users and need a trust relationship set up between an AWS-hosted directory and your on-premises directories.
* In most cases, Simple AD is the least expensive option and your best choice if you have 5,000 or fewer users and don’t need the more advanced Microsoft Active Directory features.
* AD Connector is your best choice when you want to use your existing onpremises directory with AWS cloud services.

#### AWS Key Management Service (KMS) and AWS CloudHSM

Key management is the management of cryptographic keys within a cryptosystem.

##### Overview

AWS offers two services that provide you with the ability to manage your own symmetric or asymmetric cryptographic keys:

* AWS KMS
* AWS CloudHSM

**AWS Key Management Service (AWS KMS)** is a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data.

Whether you are writing applications for AWS or using AWS cloud services, AWS KMS enables you to maintain control over who can use your keys and gain access to your encrypted data.

* *Customer Managed Keys* AWS KMS uses a type of key called a Customer Master Key (CMK) to encrypt and decrypt data. They can be used inside of AWS KMS to encrypt or decrypt up to 4 KB of data directly. They can also be used to encrypt generated data keys that are then used to encrypt or decrypt larger amounts of data outside of the service. CMKs can never leave AWS KMS unencrypted, but data keys can leave the service unencrypted.
* *Data Keys* You use data keys to encrypt large data objects within your own application outside AWS KMS. AWS KMS returns a plaintext version of the key and ciphertext that contains the key encrypted under the specified CMK.Security best practices suggest that you should remove the plaintext key from memory as soon as is practical after use.
* *Envelope Encryption* AWS KMS uses envelope encryption to protect data.
* *Encryption Context* All AWS KMS cryptographic operations accept an optional key/value map of additional contextual information.

**AWS CloudHSM** An HSM is a hardware appliance that provides secure key storage and cryptographic operations within a tamper-resistant hardware module. 

AWS CloudHSM allows you to protect your encryption keys within HSMs that are designed and validated to government standards for secure key management. 

##### Use Cases

The AWS key management services address several security needs that would require extensive effort to deploy and manage otherwise, including, but not limited to:

* Scalable Symmetric Key Distribution
* Government-Validated Cryptography

#### AWS CloudTrail

AWS CloudTrail provides visibility into user activity by recording API calls made on your account.

##### Overview

A trail is a configuration that enables logging of the AWS API activity and related events in your account.

You can create two types of trails:

* A Trail That Applies to All Regions 
* A Trail That Applies to One Region

AWS CloudTrail typically delivers log files within 15 minutes of an API call. In addition, the service publishes new log files multiple times an hour, usually about every five minutes.

##### Use Cases

* External Compliance Audits
* Unauthorized Access to Your AWS Account

### Analytics

#### Amazon Kinesis

##### Overview

Amazon Kinesis is a streaming data platform consisting of three services addressing different real-time streaming data challenges:

* Amazon Kinesis Firehose: A service enabling you to load massive volumes of streaming data into AWS
* Amazon Kinesis Streams: A service enabling you to build custom applications for more complex analysis of streaming data in real time
* Amazon Kinesis Analytics: A service enabling you to easily analyze streaming data real time with standard SQL

**Amazon Kinesis Firehose** 

![Amazon Kinesis Firehose](https://cdn-images-1.medium.com/max/1600/1*nvcEq5asDwetCdRZ2VbYyg.png)

**Amazon Kinesis Streams**

![Amazon Kinesis Streams](https://dmhnzl5mp9mj6.cloudfront.net/bigdata_awsblog/images/Markus%20Python%20image%201.png)

##### Use Cases

* Data Ingestion
* Real-Time Processing of Massive Data Streams

It’s good to remember that while Amazon Kinesis is ideally suited for ingesting and processing streams of data, it is less appropriate for batch jobs such as nightly Extract, Transform, Load (ETL) processes. Instead, consider AWS Data Pipeline.

#### Amazon Elastic MapReduce (Amazon EMR)

##### Overview

When you launch an Amazon EMR cluster, you specify several options, the most important being:

* The instance type of the nodes
* The number of nodes
* The version of Hadoop
* Additional tools or applications like Hive, Pig, Spark

There are two types of storage that can be used with Amazon EMR:

* HDFS - Amazon EMR can use Amazon EC2 instance storage or Amazon EBS for HDFS. (for persistent cluster)
* EMRFS - EMRFS is an implementation of HDFS that allows clusters to store data on Amazon S3. (for transient cluster)

A key factor driving the type of storage a cluster uses is whether the cluster is persistent or transient.

##### Use Cases

* Log Processing
* Clickstream Analysis
* Genomics and Life Sciences

#### AWS Data Pipeline

AWS Data Pipeline is a web service that helps you reliably process and move data between different AWS compute and storage services, and also on-premises data sources, at specified intervals.

##### Overview

The pipeline interacts with data stored in data nodes. 

The pipeline will execute activities that represent common scenarios, such as moving data from one location to another, running Hive queries, and so forth.

If an activity fails, retry is automatic. The activity will continue to retry up to the limit you configure. 

##### Use Cases

AWS Data Pipeline can be used for virtually any batch mode ETL process.

![Example](https://dmhnzl5mp9mj6.cloudfront.net/bigdata_awsblog/images/Wangechi_Workflow_Image_6.png)

#### AWS Import/Export

AWS Import/Export is a service that accelerates transferring large amounts of data into and out of AWS using physical storage appliances, bypassing the Internet.

##### Overview

Two features:

* **AWS Snowball** AWS Snowball uses Amazon-provided shippable storage appliances shipped through UPS. At the time of this writing, AWS Snowballs come in two sizes: 50TB and 80TB.
* **AWS Import/Export Disk** AWS Import/Export Disk supports transfers data directly onto and off of storage devices you own using the Amazon high-speed internal network. AWS Import/Export Disk has an upper limit of 16TB.

##### Use Cases

AWS Import/Export can be used for just about any situation where you have more data to move than you can get through your Internet connection in a reasonable time.

### DevOps

#### AWS OpsWorks

AWS OpsWorks supports both Linux or Windows servers, including existing Amazon EC2 instances or servers running in your own data center.

##### Overview

![Simple application server stack](https://docs.aws.amazon.com/opsworks/latest/userguide/images/php_walkthrough_arch.png)

This group of resources is typically called a stack. AWS OpsWorks provides a simple and flexible way to create and manage stacks and applications.

The stack is the core AWS OpsWorks component. It is basically a container for AWS resources that have a
common purpose and make sense to be logically managed together.

> Note: You can use AWS OpsWorks or IAM to manage user permissions. Note that the two options are not mutually exclusive; it is sometimes desirable to use both.

You define the elements of a stack by adding one or more layers. A layer represents a set of resources that serve a particular purpose.

An instance represents a single computing resource, such as an Amazon EC2 instance. It defines the resource’s basic configuration, such as operating system and size.

You store applications and related files in a repository. Each application is represented by an app, which specifies the application type and contains the information that is needed to deploy the application from the repository to your instances, such as the repository URL and password.

AWS OpsWorks sends all of your resource metrics to Amazon CloudWatch.

##### Use Cases

* Host Multi-Tier Web Applications
* Support Continuous Integration

#### AWS CloudFormation

##### Overview

When you use AWS CloudFormation, you work with templates and stacks.

You create AWS CloudFormation templates to define your AWS resources and their properties. A template is a text file whose format complies with the JSON standard.

When you use AWS CloudFormation, you manage related resources as a single unit called a stack.

![creating a stack workflow](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/images/create-stack-diagram.png)

To update a stack, create a change set by submitting a modified version of the original stack template, different input parameter values, or both.

![updating a stack workflow](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/images/update-stack-diagram.png)

> Note: If you want to delete a stack but still retain some resources in that stack, you can use a deletion policy to retain those resources. If a resource has no deletion policy, AWS CloudFormation deletes the resource by default.

##### Use Cases

* Quickly Launch New Test Environments
* Reliably Replicate Configuration Between Environments
* Launch Applications in New AWS Regions

#### AWS Elastic Beanstalk

Developers can simply upload their application code, and the service automatically handles all of the details, such as resource provisioning, load balancing, Auto Scaling, and monitoring.

##### Overview

In AWS Elastic Beanstalk, an application is conceptually similar to a folder.

Key components:

* An *application version* refers to a specific, labeled iteration of deployable code for a web application.
* An *environment* is an application version that is deployed onto AWS resources. 
* An *environment configuration* identifies a collection of parameters and settings that define how an environment and its associated resources behave.

An *AWS Elastic Beanstalk application* is the logical collection of these AWS Elastic Beanstalk components.

##### Key Features

With AWS Elastic Beanstalk, organizations can deploy an application quickly while retaining as much control as they want to have over the underlying infrastructure.

#### AWS Trusted Advisor

AWS Trusted Advisor inspects your AWS environment and makes recommendations when opportunities exist to save money, improve system availability and performance, or help close security gaps.

AWS Trusted Advisor provides best practices in four categories: cost optimization, security, fault tolerance, and performance improvement. 

![AWS Trusted Advisor Console dashboard](https://d3ulk6ur3a3ha.cloudfront.net/Image_Thumbs/TrustedAdvisor/ConsoleVersion/dashboard.png)

All AWS customers have access to four AWS Trusted Advisor checks at no cost. The four standard AWS Trusted Advisor checks are:

* Service Limits
* Security Groups–Specific Ports Unrestricted
* IAM Use
* MFA on Root Account 

#### AWS Config

AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance.

##### Overview

When you turn on AWS Config, it first discovers the supported AWS resources that exist in your account and generates a configuration item for each resource. A configuration item represents a point-in-time view of the various attributes of a supported AWS resource that exists in your account.

AWS Config will generate configuration items when the configuration of a resource changes, and it maintains historical records of the configuration items of your resources from the time you start the configuration recorder. The configuration recorder stores the configurations of the supported resources in your account as configuration items.

An AWS Config Rule represents desired configuration settings for specific AWS resources or for an entire AWS
account.

##### Use cases

* Discovery
* Change Management
* Continuous Audit and Compliance
* Troubleshooting
* Security and Incident Analysis

##### Key features

AWS Config resolves this previous need and automatically records resource configuration information and will evaluate any rules that are triggered by a change. 

### Exam Essentials

* Know the basic use cases for amazon CloudFront.
* Know how amazon CloudFront works.
* Know how to create an amazon CloudFront distribution and what types of origins are supported.
* Know how to use amazon CloudFront for dynamic content and multiple origins.
* Know what mechanisms are available to serve private content through amazon CloudFront.
* Know the three configurations of AWS storage gateway and their use cases.
* Understand the value of AWS Directory Service.
* Know the AWS Directory Service Directory types. 
* Know when you should use AWS Directory Service for Microsoft Active Directory.
* Understand key management.
* Understand when you should use AWS KMS. 
* Understand when you should use AWS CloudHSM.
* Understand the value of AWS CloudTrail.
* Know the three services of Amazon kinesis and their use cases.
* Know what service Amazon EMR provides.
* Know the difference between persistent and transient clusters.
* Know the use cases for Amazon EMR.
* Know the use cases for AWS data pipeline.
* Know the types of AWS import/export services and the possible sources/destinations of each.
* Understand the basics of AWS opsworks.
* Understand the value of AWS cloudformation. 
* Understand the value of AWS elastic beanstalk.
* Understand the components of AWS elastic beanstalk.
* Understand the value of AWS config.




<span id="chapter-12"></span>
## Chapter 12 - Security on AWS

### Shared Responsibility Model

![The shared responsibility model](https://d1.awsstatic.com/security-center/Shared_Responsibility_Model_V2.59d1eccec334b366627e9295b304202faf7b899b.jpg)

### AWS Compliance Program

### AWS Global Infrastructure Security

#### Physical and Environmental Security

* Fire Detection and Suppression
* Power
* Climate and Temperature
* Management
* Storage Device Decommissioning

#### Business Continuity Management

* Availability
* Incident Response
* Communication

#### Network Security

* Secure Network Architecture
* Secure Access Points
* Transmission Protection

#### Network Monitoring and Protection

* Distributed Denial of Service (DDoS) Attacks
* Man in the Middle (MITM) Attacks
* IP Spoofing
* Port Scanning
* Packet Sniffing by Other Tenants

> Tip: Attacks such as Address Resolution Protocol (ARP) cache poisoning do not work within Amazon EC2 and Amazon VPC.

### AWS Account Security Features

#### AWS Credentials

| Credential Type | Use | Description |
| :-------------- | :-- | :---------- |
| Passwords       | AWS root account or IAM user account login to the AWS Management Console | A string of characters used to log in to your AWS account or IAM account. AWS passwords must be a minimum of 6 characters and may be up to 128 characters. |
| MFA             | AWS root account or IAM user account login to the AWS Management Console | A six-digit, single-use code that is required in addition to your password to log in to your AWS account or IAM user account. |
| Access Keys     | Digitally-signed requests to AWS APIs | Includes an access key ID and a secret access key. You use access keys to sign programmatic requests digitally that you make to AWS. |
| Key Pairs       | SSH login to Amazon EC2 instances Amazon CloudFront-signed URLs | A key pair is required to connect to an Amazon EC2 instance launched from a public AMI. The keys that Amazon EC2 uses are 1024-bit SSH-2 RSA keys. You can have a key pair generated automatically for you when you launch the instance, or you can upload your own. |
| X.509 Certificates | Digitally signed SOAP requests to AWS APIs SSL server certificates for HTTPS | X.509 certificates are only used to sign SOAP-based requests (currently used only with Amazon Simple Storage Service [Amazon S3]). You can have AWS create an X.509 certificate and private key that you can download, or you can upload your own certificate by using the Security Credentials page. |

### AWS Cloud Service-Specific Security

#### Compute Services

##### Amazon Elastic Compute Cloud (Amazon EC2) Security

* Multiple Levels of Security
* The Hypervisor


