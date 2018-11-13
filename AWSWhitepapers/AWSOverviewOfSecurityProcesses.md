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
