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

### Loose Coupling

As application complexity increases, a desirable attribute of an IT system is that itcan be broken into smaller, loosely coupled components.

#### Well-Defined Interfaces

A way to reduce interdependencies in a system is to allow the various components to interact with each other only through specific, technologyagnostic interfaces (e.g., RESTful APIs). In that way, technical implementation detail is hidden so that teams can modify the underlying implementation without affecting other components.

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

#### Service Discovery

Applications that are deployed as a set of smaller services will depend on the ability of those services to interact with each other. Apart from hiding complexity, this also allows infrastructure details to change at any time.

For an Amazon EC2 hosted service a simple way to achieve service discovery is through the Elastic Load Balancing service.

Another option would be to use a service registration and discovery method to allow retrieval of the endpoint IP addresses and port number of any given service. Because service discovery becomes the glue between the components, it is important that it is highly available and reliable.

#### Asynchronous Integration

Asynchronous integration is another form of loose coupling between services. This model is suitable for any interaction that does not need an immediate response and where an acknowledgement that a request has been registered will suffice. It involves one component that generates events and another that
consumes them. 

A front end application inserts jobs in a queue system like Amazon SQS. A back-end system retrieves those jobs and processes them at its own pace.

An API generates events and pushes them into Amazon Kinesis streams. A back-end application processes these events in batches to create aggregated time-series data stored in a database.

Multiple heterogeneous systems use Amazon SWF to communicate the flow of work between them without directly interacting with each other.

AWS Lambda functions can consume events from a variety of AWS sources (e.g., Amazon DynamoDB update streams, Amazon S3 event notifications, etc.). 

#### Graceful Failure

Another way to increase loose coupling is to build applications in such a way that they handle component failure in a graceful manner.

A request that fails can be retried with an exponential backoff and Jitter strategy or it could be stored in a queue for later processing. 

The Amazon Route 53 DNS failover feature also gives you the ability to monitor your website and automatically route your visitors to a backup site if your primary site becomes unavailable. 

### Services, Not Servers

#### Managed Services

On AWS, there is a set of services that provide building blocks that developers can consume to power their applications. 

#### Serverless Architectures

It is possible to build both event-driven and synchronous services for mobile, web, analytics, and the Internet of Things (IoT) without managing any server infrastructure.

You can upload your code to the AWS Lambda compute service and the service can run the code on your behalf using AWS infrastructure. 

By using Amazon API Gateway, you can develop virtually infinitely scalable synchronous APIs powered by AWS Lambda.

When it comes to mobile apps, there is one more way to reduce the surface of a server-based infrastructure. You can utilize Amazon Cognito, so that you don’t have to manage a back end solution to handle user authentication, network state, storage, and sync.

### Databases

#### Relational Databases

RDS.

##### Scalability

Relational databases can scale vertically (e.g., by upgrading to a larger Amazon RDS DB instance or adding more and faster storage). In addition, consider the use of Amazon RDS for Aurora, which is a database engine designed to deliver much higher throughput compared to standard MySQL running on the same hardware. For read-heavy applications, you can also horizontally scale beyond the capacity constraints of a single DB instance by creating one or more read replicas. 

Relational database workloads that need to scale their write capacity beyond the constraints of a single DB instance require a different approach called data partitioning or sharding. With this model, data is split across multiple database schemas each running in its own autonomous primary DB instance

##### High Availability

For any production relational database, we recommend the use of the Amazon RDS Multi-AZ deployment feature, which creates a synchronously replicated standby instance in a different Availability Zone (AZ). 

##### Anti-Patterns

If your application primarily indexes and queries data with no need for joins or complex transactions, consider a NoSQL database instead. If you have large binary files (audio, video, and image), it will be more efficient to store the actual files in the Amazon Simple Storage Service (Amazon S3) and only hold the metadata for the files in your database. 

#### NoSQL Databases

DynamoDB.

##### Scalability

NoSQL database engines will typically perform data partitioning and replication to scale both the reads and the writes in a horizontal fashion. Amazon DynamoDB in particular manages table partitioning for you automatically, adding new partitions as your table grows in size or as read- and write-provisioned capacity changes.

##### High Availability

The Amazon DynamoDB service synchronously replicates data across three facilities in an AWS region.

##### Anti-Patterns

If your schema cannot be denormalized and your application requires joins or complex transactions, consider a relational database instead. Or S3.

#### Data Warehouse

Redshift.

##### Scalability

Amazon Redshift achieves efficient storage and optimum query performance through a combination of massively parallel processing (MPP), columnar data storage, and targeted data compression encoding schemes. The Amazon Redshift MPP architecture enables you to increase performance by increasing the number of nodes in your data warehouse cluster.

##### High Availability

We recommend that you deploy production workloads in multi-node clusters in which data written to a node is automatically replicated to other nodes within the cluster. Data is also continuously backed up to Amazon S3. 

##### Anti-Patterns

If you expect a high concurrency workload that generally involves reading and writing all of the columns for a small number of records at a time you should instead consider using Amazon RDS or Amazon DynamoDB. 

#### Search

CloudSearch & Elasticsearch.

On the one hand, Amazon CloudSearch is a managed service that requires little configuration and will scale automatically. On the other hand, Amazon ES offers an open source API and gives you more control over the configuration details. 

##### Scalability

Both Amazon CloudSearch and Amazon ES use data partitioning and replication to scale horizontally. The difference is that Amazon CloudSearch handles the number of partitions and replicas you will need automatically. 

##### High Availability

Both services provide features that store data redundantly across Availability Zones. 

### Removing Single Points of Failure

A system is highly available when it can withstand the failure of an individual or multiple components.

#### Introducing Redundancy

Single points of failure can be removed by introducing redundancy, which is having multiple resources for the same task. Redundancy can be implemented in either standby or active mode.

#### Detect Failure

You can use services like ELB and Amazon Route53 to configure health checks and mask failure by routing traffic to healthy endpoints. In addition, Auto Scaling can be configured to automatically replace unhealthy nodes. You can also replace unhealthy nodes using the Amazon EC2 autorecovery feature or services such as AWS OpsWorks and AWS Elastic Beanstalk. 

#### Durable Data Storage

Data replication is the technique that introduces redundant copies of data. It can help horizontally scale read capacity, but it also increase data durability and availability.

Synchronous replication only acknowledges a transaction after it has been durably stored in both the primary location and its replicas. 

Asynchronous replication decouples the primary node from its replicas at the expense of introducing replication lag.

Quorum-based replication combines synchronous and asynchronous replication to overcome the challenges of large-scale distributed database systems. 

#### Automated Multi-Data Center Resilience

Many of the higher level services on AWS are inherently designed according to the Multi-AZ principle. For example, Amazon RDS provides high availability and automatic failover support for DB instances using Multi-AZ deployments, while with Amazon S3 and Amazon DynamoDB your data is redundantly stored across multiple facilities.

#### Fault Isolation and Traditional Horizontal Scaling

If a particular request happens to trigger a bug that causes the system to fail over, then the caller may trigger a cascading failure by repeatedly trying the same request against all instances.

One fault-isolating improvement you can make to traditional horizontal scaling is called sharding. Similar to the technique traditionally used with data storage systems, instead of spreading traffic from all customers across every node, you can group the instances into shards. For example, if you have eight instances for your service, you might create four shards of two instances each (two instances for some redundancy within each shard) and distribute each customer to a specific shard. 

However, there will still be affected customers, so the key is to make the client fault tolerant. If the client can try every endpoint in a set of sharded resources, until one succeeds, you get a dramatic improvement. This technique is called shuffle sharding