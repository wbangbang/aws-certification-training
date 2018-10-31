# Architecting for the Cloud: AWS Best Practices

Source: https://d0.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf

## The Cloud Computing Difference

### IT Assets Become Programmable Resources

On AWS, servers, databases, storage, and higher-level application components can be instantiated within seconds. You can treat these as temporary and disposable resources, free from the inflexibility and constraints of a fixed and finite IT infrastructure.

### Global, Available, and Unlimited Capacity

For global applications, you can reduce latency to end users around the world by using the Amazon CloudFront content delivery network. It is also much easier to operate production applications and databases across multiple data centers to achieve high availability and fault tolerance. 

### Higher Level Managed Services

These services are managed by AWS, which can lower operational complexity and cost. AWS managed services are designed for scalability and high availability, so they can reduce risk for your implementations.

### Security Built In

Since AWS assets are programmable resources, your security policy can be formalized and embedded with the design of your infrastructure. 

## Design Principles

### Scalability

Systems that are expected to grow over time need to be built on top of a scalable architecture. Such an architecture can support growth in users, traffic, or data size with no drop in performance. It should provide that scale in a linear manner where adding extra resources results in at least a proportional increase in ability to serve additional load. 

#### Scaling Vertically

Scaling vertically takes place through an increase in the specifications of an individual resource (e.g., upgrading a server with a larger hard drive or a faster CPU).

#### Scaling Horizontally

Scaling horizontally takes place through an increase in the number of resources (e.g., adding more hard drives to a storage array or adding more servers to support an application). 

##### Stateless Applications

A stateless application is an application that needs no knowledge of previous interactions and stores no session information. Such an example could be an application that, given the same input, provides the same response to any end user. A stateless application can scale horizontally since any request can be serviced by any of the available compute resources (e.g., EC2 instances, AWS Lambda functions).  Those resources do not need to be aware of the presence of their peers – all that is required is a way to distribute the workload to them.

> How to distribute load to multiple nodes
> 
> Push model: A popular way to distribute a workload is through the use of a load balancing solution like the Elastic Load Balancing (ELB) service. An alternative approach would be to implement a DNS round robin (e.g., with Amazon Route 53), where DNS responses return an IP address from a list of valid hosts in a round robin fashion.
> 
> Pull model: In a pull model, tasks that need to be performed or data that need to be processed could be stored as messages in a queue using Amazon Simple Queue Service (Amazon SQS) or as a streaming data solution like Amazon Kinesis. 

##### Stateless Components

Inevitably, there will be layers of your architecture that you won’t turn into stateless components. First, by definition, databases are stateful. In addition, many legacy applications were designed to run on a single server by relying on local compute resources.  

You might still be able to scale those components horizontally by distributing load to multiple nodes with “session affinity.” In this model, you bind all the transactions of a session to a specific compute resource. Importantly, session affinity cannot be guaranteed.

> How to implement session affinity
> 
> For HTTP/S traffic, session affinity can be achieved through the “sticky sessions” feature of ELB. Elastic Load Balancing will attempt to use the same server for that user for the duration of the session.
> 
> Another option, if you control the code that runs on the client, is to use clientside load balancing. 

##### Distributed Processing

Use cases that involve processing of very large amounts of data (e.g., anything that can’t be handled by a single compute resource in a timely manner) require a distributed processing approach.

> How to implement distributed processing
> 
> Offline batch jobs can be horizontally scaled by using a distributed data processing engine like Apache Hadoop.
> 
>  For real-time processing of streaming data, Amazon Kinesis partitions data in multiple shards that can then be consumed by multiple Amazon EC2 or AWS Lambda resources to achieve scalability.

### Disposable Resources Instead of Fixed Servers

#### Instantiating Compute Resources

It is important that you make this an automated and repeatable process that avoids long lead times and is not prone to human error.

##### Bootstrapping

When you launch an AWS resource like an Amazon EC2 instance or Amazon Relational Database (Amazon RDS) DB instance, you start with a default configuration. You can then execute automated bootstrapping actions. You can parameterize configuration details that vary between different environments (e.g., production, test, etc.) so that the same scripts can be reused without modifications.

You can use user data scripts and cloud-init6 directives or AWS OpsWorks lifecycle events to automatically set up new EC2 instances. through custom scripts and the AWS APIs, or through the use of AWS CloudFormation support for AWS Lambda-backed custom resources, it is possible to write provisioning logic that acts on almost any AWS resource. 

##### Golden Images

Certain AWS resource types like Amazon EC2 instances, Amazon RDS DB instances, Amazon Elastic Block Store (Amazon EBS) volumes, etc., can be launched from a golden image: a snapshot of a particular state of that resource. When compared to the bootstrapping approach, a golden image results in faster start times and removes dependencies to configuration services or third-party repositories. 

You can customize an Amazon EC2 instance and then save its configuration by creating an Amazon Machine Image (AMI). If you have an existing on-premises virtualized environment, you can use VM Import/Export from AWS to convert a variety of virtualization formats to an AMI. You can also find and use prebaked shared AMIs provided either by AWS or third parties in the AWS Community AMI catalog or the AWS Marketplace.

AWS Elastic Beanstalk and the Amazon EC2 Container Service (Amazon ECS) support Docker, which is another option, and enable you to deploy and manage multiple Docker containers across a cluster of Amazon EC2 instances.

##### Hybrid

Items that do not change often or that introduce external dependencies will typically be part of your golden image. Items that change often or differ between your various environments can be set up dynamically through bootstrapping actions.

AWS Elastic Beanstalk follows the hybrid model. It provides preconfigured run time environments (each initiated from its own AMI) but allows you to run bootstrap actions and configure environmental variables to parameterize the environment differences.

#### Infrastructure as Code

AWS CloudFormation - You can describe the AWS resources, and any associated dependencies or run time parameters, required to run your application. Your CloudFormation templates can live with your application in your version control repository, allowing architectures to be reused and production environments to be reliably cloned for testing.

### Automation

**AWS Elastic Beanstalk** is the fastest and simplest way to get an application up and running on AWS. 

**Amazon EC2 Auto recovery**: You can create an Amazon CloudWatch alarm that monitors an Amazon EC2 instance and automatically recovers it if it becomes impaired. This feature is only available for applicable instance configurations. 

**Auto Scaling**: With Auto Scaling, you can maintain application availability and scale your Amazon EC2 capacity up or down automatically according to conditions you define. 

**Amazon CloudWatch Alarms**: You can create a CloudWatch alarm that sends an Amazon Simple Notification Service (Amazon SNS) message when a particular metric goes beyond a specified threshold for a specified number of periods.

**Amazon CloudWatch Events**: The CloudWatch service delivers a near real-time stream of system events that describe changes in AWS resources.

**AWS OpsWorks Lifecycle events**: AWS OpsWorks supports continuous configuration through lifecycle events that automatically update your instances’ configuration to adapt to environment changes. 

**AWS Lambda Scheduled events**: These events allow you to create a Lambda function and direct AWS Lambda to execute it on a regular schedule.

