# Amazon Web Services: Overview of Security Processes

Source: https://d1.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf

## Shared Security Responsibility Model

When you move computer systems and data to the cloud, security responsibilities become shared between you and your cloud service provider. In this case, AWS is responsible for securing the underlying infrastructure that supports the cloud, and you’re responsible for anything you put on the cloud or connect to the cloud. 

![](https://cdn-images-1.medium.com/max/1200/0*42-EBqDIao1FCOGr.png)

### AWS Security Responsibilities

In addition to protecting this global infrastructure, AWS is responsible for the security configuration of its products that are considered managed services. For these services, AWS will handle basic security tasks like guest operating system (OS) and database patching, firewall configuration, and disaster recovery. For most of these managed services, all you have to do is configure logical access controls for the resources and protect your account credentials. 

### Customer Security Responsibilities

AWS products that fall into the well-understood category of Infrastructure as a Service (IaaS)—such as Amazon EC2, Amazon VPC, and Amazon S3—are completely under your control and require you to perform all of the necessary security configuration and management tasks. 

With managed services, you don’t have to worry about launching and maintaining instances, patching the guest OS or database, or replicating databases—AWS handles that for you. But as with all services, you should protect your AWS Account credentials and set up individual user accounts with Amazon Identity and Access Management (IAM). We also recommend using multi-factor authentication (MFA) with each account, requiring the use of SSL/TLS to communicate with your AWS resources, and setting up API/user activity logging with AWS CloudTrail. 

## AWS Global Infrastructure Security

The AWS global infrastructure includes the facilities, network, hardware, and operational software (e.g., host OS, virtualization software, etc.) that support the provisioning and use of these resources. 

### AWS Compliance Program

The IT infrastructure that AWS provides to its customers is designed and managed in alignment with security best practices and a variety of IT security standards, including:

* SOC 1/SSAE 16/ISAE 3402 (formerly SAS 70)
* SOC 2
* SOC 3
* FISMA, DIACAP, and FedRAMP
* DOD CSM Levels 1-5
* PCI DSS Level 1
* ISO 9001 / ISO 27001
* ITAR
* FIPS 140-2
* MTCS Level 3

### Physical and Environmental Security

#### Fire Detection and Suppression

#### Power

#### Climate and Temperature

#### Management

#### Storage Device Decommissioning

### Business Continuity Management

Amazon’s infrastructure has a high level of availability and provides customers the features to deploy a resilient IT architecture. 

#### Availability

#### Incident Response

#### Company-Wide Executive Review

#### Communication

### Network Security

#### Secure Network Architecture

#### Secure Access Points

#### Transmission Protection

#### Amazon Corporate Segregation

Logically, the AWS Production network is segregated from the Amazon Corporate network by means of a complex set of network security / segregation devices. Approved AWS personnel then connect to the AWS network through a bastion host that restricts access to network devices and other cloud components, logging all activity for security review. 

#### Fault-Tolerant Design

#### Network Monitoring and Protection

### AWS Access

#### Account Review and Audit

Accounts are reviewed every 90 days; explicit re-approval is required or access to the resource is automatically revoked. 

#### Background Checks

#### Credentials Policy

Passwords must be complex and are forced to be changed every 90 days.

### Secure Design Principles

### Change Management

Routine, emergency, and configuration changes to existing AWS infrastructure are authorized, logged, tested, approved, and documented in accordance with industry norms for similar systems.

#### Software

AWS applies a systematic approach to managing change so that changes to customer-impacting services are thoroughly reviewed, tested, approved, and well-communicated.

#### Infrastructure

Amazon’s Corporate Applications team develops and manages software to automate IT processes for UNIX/Linux hosts in the areas of third-party software delivery, internally developed software, and configuration management. 

### AWS Account Security Features

This includes credentials for access control, HTTPS endpoints for encrypted data transmission, the creation of separate IAM user accounts, user activity logging for security monitoring, and Trusted Advisor security checks. 

#### AWS Credentials 

* Passwords
* Multi-Factor Authetication
* Access Keys
* Key Pairs
* X.509 Certificates

### Individual User Accounts

### Secure HTTPS Access Points

### Security Logs

AWS CloudTrail provides a log of events within your account. For each event, you can see what service was accessed, what action was performed, and who made the request.

### AWS Trusted Advisor Security Checks

### AWS Config Security Checks

AWS Config is a continuous monitoring and assessment service that records changes to the configuration of your AWS resources. Using Config Rules, you can run continuous assessment checks on your resources to verify that they comply with your own security policies, industry best practices, and compliance regimes such as PCI/HIPAA.

## AWS Service-Specific Security

### Compute Services

#### Amazon Elastic Compute Cloud (Amazon EC2) Security

* Multiple Levels of Security - the operating system (OS) of the host platform, the virtual instance OS or guest OS, a firewall, and signed API calls. 
* The Hypervisor - Amazon EC2 currently utilizes a highly customized version of the Xen hypervisor, taking advantage of paravirtualization (in the case of Linux guests). 
* Instance Isolation - Different instances running on the same physical machine are isolated from each other via the Xen hypervisor. In addition, the AWS firewall resides within the hypervisor layer, between the physical network interface and the instance's virtual interface. 

![](https://docplayer.net/docs-images/24/3785024/images/22-0.png)
![](https://d1.awsstatic.com/aws-answers/answers-images/security-group-config.17423baeced21997af7a131760196cfed6f39bb9.png)

* Elastic Block Storage (Amazon EBS) Security - Amazon Elastic Block Storage (EBS) allows you to create storage volumes from 1 GB to 16 TB that can be mounted as devices by Amazon EC2 instances. Amazon EBS volume access is restricted to the AWS Account that created the volume, and to the users under the AWS Account created with AWS IAM if the user has been granted access to the EBS operations.

#### Auto Scaling Security

Auto Scaling requires that every request made to its control API be authenticated so only authenticated users can access and manage Auto Scaling. You can use roles within IAM, so that any new instances launched with a role will be given credentials automatically.

### Networking Services

#### Amazon Elastic Load Balancing Security

Elastic Load Balancing has all the advantages of an on-premises load balancer, plus several security benefits:

* Takes over the encryption and decryption work from the Amazon EC2 instances and manages it centrally on the load balancer
* Offers clients a single point of contact, and can also serve as the first line of defense against attacks on your network
* When used in an Amazon VPC, supports creation and management of security groups associated with your Elastic Load Balancing to provide additional networking and security options
* Supports end-to-end traffic encryption using TLS (previously SSL) on those networks that use secure HTTP (HTTPS) connections. When TLS is used, the TLS server certificate used to terminate client connections can be managed centrally on the load balancer, rather than on every individual instance.

#### Amazon Virtual Private Cloud (Amazon VPC) Security

AWS offers a variety of VPC architecture templates with configurations that provide varying levels of public access:

* VPC with a single public subnet only.
* VPC with public and private subnets.
* VPC with public and private subnets and hardware VPN access. 
* VPC with private subnet only and hardware VPN access.

Note that you must create VPC security groups specifically for your Amazon VPC; any Amazon EC2 security groups you have created will not work inside your Amazon VPC.

Each Amazon VPC is a distinct, isolated network within the cloud; network traffic within each Amazon VPC is isolated from all other Amazon VPCs.

**API Access:** Calls to create and delete Amazon VPCs, change routing, security group, and network ACL parameters, and perform other functions are all signed by your Amazon Secret Access Key, which could be either the AWS Account’s Secret Access Key or the Secret Access key of a user created with AWS IAM. 

**Subnets and Route Tables:** You create one or more subnets within each Amazon VPC; each instance launched in the Amazon VPC is connected to one subnet. Each subnet in an Amazon VPC is associated with a routing table, and all network traffic leaving the subnet is processed by the routing table to determine the destination.

**Firewall (Security Groups):** Like Amazon EC2, Amazon VPC supports a complete firewall solution enabling filtering on both ingress and egress traffic from an instance. The default group enables inbound communication from other members of the same group and outbound communication to any destination. 

**Network Access Control Lists:** These are stateless traffic filters that apply to all traffic inbound or outbound from a subnet within Amazon VPC. 

![](https://dome9.com/wp-content/uploads/2015/07/blog-pic1.png)

**Virtual Private Gateway:** A virtual private gateway enables private connectivity between the Amazon VPC and another network.

**Internet Gateway:** An Internet gateway may be attached to an Amazon VPC to enable direct connectivity to Amazon S3, other AWS services, and the Internet. 

**Dedicated Instances:** An Amazon VPC can be created with ‘dedicated’ tenancy, so that all instances launched into the Amazon VPC will utilize this feature.

**Elastic Network Interfaces:** Each Amazon EC2 instance has a default network interface that is assigned a private IP address on your Amazon VPC network. You can create and attach an additional network interface, known as an elastic network interface (ENI), to any Amazon EC2 instance in your Amazon VPC for a total of two network interfaces per instance. 

Additional Network Access Control with EC2-VPC
When you launch an instance into a default VPC using EC2-VPC, we do the following to set it up for you:

* Create a default subnet in each Availability Zone
* Create an Internet gateway and connect it to your default VPC
* Create a main route table for your default VPC with a rule that sends all traffic destined for the Internet to the Internet gateway
* Create a default security group and associate it with your default VPC
* Create a default network access control list (ACL) and associate it with your default VPC
* Associate the default DHCP options set for your AWS account with your default VPC

Note the difference between EC2-Classic and EC2-VPC.

#### Amazon Route 53 Security

The distributed nature of the AWS DNS servers helps ensure a consistent ability to route your end users to your application. Route 53 also helps ensure the availability of your website by providing health checks and DNS failover capabilities. 

Like all AWS Services, Amazon Route 53 requires that every request made to its control API be authenticated so only authenticated users can access and manage Route 53.

#### Amazon CloudFront Security

Like all AWS Services, Amazon Route 53 requires that every request made to its control API be authenticated so only authenticated users can access and manage Route 53. Additionally, the Amazon CloudFront control API is only accessible via SSL-enabled endpoints.

There is no guarantee of durability of data held in Amazon CloudFront edge locations.

If you want control over who is able to download content from Amazon CloudFront, you can enable the service’s private content feature. This feature has two components: the first controls how content is delivered from the Amazon CloudFront edge location to viewers on the Internet. The second controls how the Amazon CloudFront edge locations access objects in Amazon S3.

To control access to the original copies of your objects in Amazon S3, Amazon CloudFront allows you to create one or more “Origin Access Identities” and associate these with your distributions. When an Origin Access Identity is associated with an Amazon CloudFront distribution, the distribution will use that identity to retrieve objects from Amazon S3.

To control who is able to download objects from Amazon CloudFront edge locations, the service uses a signed-URL verification system.

#### AWS Direct Connect Security

With AWS Direct Connect, you can provision a direct link between your internal network and an AWS region using a high-throughput, dedicated connection. With this dedicated connection in place, you can then create virtual interfaces directly to the AWS cloud (for example, to Amazon EC2 and Amazon S3) and Amazon VPC.

### Storage Services

#### Amazon Simple Storage Service (Amazon S3) Security

**Data Access**

* Identity and Access Management (IAM) Policies.
* Access Control Lists (ACLs).
* Bucket Policies.

| Type of Access Control | AWS Account-Level Control? | User-Level Control? |
| :--------------------- | :------------------------- | :------------------ |
| IAM Policies           | No                         | Yes                 |
| ACLs                   | Yes                        | No                  |
| Bucket Policies        | Yes                        | Yes                 |

Amazon S3 also gives developers the option to use query string authentication, which allows them to share Amazon S3 objects through URLs that are valid for a predefined period of time.

**Data Transfer**

For maximum security, you can securely upload/download data to Amazon S3 via the SSL encrypted endpoints. 

**Data Storage**

* Client-side encryption
* Server-side encryption 

> Note: Metadata, which you can include with your object, is not encrypted. 

**Data Durability and Reliability**

To help provide durability, Amazon S3 PUT and COPY operations synchronously store customer data across multiple facilities before returning SUCCESS. Amazon S3 provides further protection via Versioning. 

**Access Logs**

An Amazon S3 bucket can be configured to log access to the bucket and objects within it. 

**Cross-Origin Resource Sharing (CORS)**

AWS customers who use Amazon S3 to host static web pages or store objects used by other web pages can load content securely by configuring an Amazon S3 bucket to explicitly enable cross-origin requests. 

#### AWS Glacier Security

**Data Upload**

To achieve even greater security, you can securely upload/download data to Amazon Glacier via the SSL-encrypted endpoints. 

**Data Retrieval**

You can retrieve an entire archive or several files from an archive. 

**Data Storage**

Glacier performs regular, systematic data integrity checks and is built to be automatically self-healing.

**Data Access**

To control access to your data in Amazon Glacier, you can use AWS IAM to specify which users within your account have rights to operations on a given vault.

#### AWS Storage Gateway Security

Data is asynchronously transferred from your on-premises storage hardware to AWS over SSL.

#### AWS Import/Export Security

Like all other AWS services, the AWS Import/Export service requires that you securely identify and authenticate your storage device. For added protection, you can encrypt the data on your device before you ship it to AWS. After the import is complete, AWS Import/Export will erase the contents of your storage device to safeguard the data during return shipment.

#### Amazon Elastic File System Security

**Data Access**

When using Amazon EFS, you specify Amazon EC2 security groups for your EC2 instances and security groups for the EFS mount targets associated with the file system. Security groups act as a firewall, and the rules you add define the traffic flow. All Amazon EFS file systems are owned by an AWS Account. 

**Data Durability and Reliability**

All data and metadata is stored across multiple Availability Zones. EFS provides strong consistency by synchronously replicating data across Availability Zones.

**Data Sanitization**

Amazon EFS is designed so that when you delete data from a file system, that data will never be served again.

### Database Services

#### Amazon DynamoDB Security

You can create a database table that can store and retrieve any amount of data, and serve any level of request traffic. All data items are stored on Solid State Drives (SSDs) and are automatically replicated across multiple availability zones in a region to provide built-in high availability and data durability.

To control who can use the DynamoDB resources and API, you set up permissions in AWS IAM. In addition to controlling access at the resource-level with IAM, you can also control access at the database level—you can create database-level permissions that allow or deny access to items (rows) and attributes (columns) based on the needs of your application. 

Users can sign in to an identity provider and then obtain temporary security credentials from AWS Security Token Service (AWS STS). AWS STS returns temporary AWS credentials to the application and allows it to access the specific DynamoDB table.

#### Amazon Relational Database Service (Amazon RDS) Security
