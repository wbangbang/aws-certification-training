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