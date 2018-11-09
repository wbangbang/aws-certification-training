# Amazon Web Services: Overview of Security Processes

Source: https://d1.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf

## Shared Security Responsibility Model

When you move computer systems and data to the cloud, security responsibilities become shared between you and your cloud service provider. In this case, AWS is responsible for securing the underlying infrastructure that supports the cloud, and you’re responsible for anything you put on the cloud or connect to the cloud. 

![](https://cdn-images-1.medium.com/max/1200/0*42-EBqDIao1FCOGr.png)

### AWS Security Responsibilities

In addition to protecting this global infrastructure, AWS is responsible for the security configuration of its products that are considered managed services. For these services, AWS will handle basic security tasks like guest operating system (OS) and database patching, firewall configuration, and disaster recovery. For most of these managed services, all you have to do is configure logical access controls for the resources and protect your account credentials. 

### Customer Security Responsibilities

AWS products that fall into the well-understood category of Infrastructure as a Service (IaaS)—such as Amazon EC2, Amazon VPC, and Amazon S3—are completely under your control and require you to perform all of the necessary security configuration and management tasks. 