# Amazon S3 FAQ

Source: https://aws.amazon.com/s3/faqs/

## General

* Amazon S3 is object storage built to store and retrieve any amount of data from anywhere on the Internet. It’s a simple storage service that offers an extremely durable, highly available, and infinitely scalable data storage infrastructure at very low costs.
* You can store virtually any kind of data in any format. 
* The total volume of data and number of objects you can store are unlimited. 
* Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 terabytes. Amazon S3 offers the following options:
	* With a single PUT operation, you can upload objects up to 5 GB in size.
	* Using the multipart upload API, you can upload large objects, from 5 MB up to 5 TB.
* There are four highly durable storage classes 
	* Amazon S3 Standard for general purpose storage of frequently accessed data
	* Amazon S3 Standard-Infrequent Access or Amazon S3 One Zone-Infrequent Access for long-lived, but less frequently accessed data
	* Amazon Glacier for long-term archive. 
* Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data. Keys can be any string, and they can be constructed to mimic hierarchical attributes. Alternatively, you can use S3 Object Tagging to organize your data across all of your S3 buckets and/or prefixes. 

## AWS Regions

* For S3 Standard, S3 Standard-IA, and Amazon Glacier storage classes, your objects are automatically stored across multiple devices spanning a minimum of three Availability Zones, each separated by miles across an AWS Region. Objects stored in the S3 One Zone-IA storage class are stored redundantly within a single Availability Zone in the AWS Region you select. 

## Billing

* With Amazon S3, you pay only for what you use. We charge less where our costs are less. Some prices vary across Amazon S3 Regions. There is no Data Transfer charge for data transferred within an Amazon S3 Region via a COPY request.

## Security

* Customers may use four mechanisms for controlling access to Amazon S3 resources: Identity and Access Management (IAM) policies, bucket policies, Access Control Lists (ACLs), and Query String Authentication.
* Customers can optionally configure an Amazon S3 bucket to create access log records for all requests made against it.
* You can choose to encrypt data using SSE-S3, SSE-C, SSE-KMS, or a client library.
* An Amazon VPC Endpoint for Amazon S3 is a logical entity within a VPC that allows connectivity only to S3. The VPC Endpoint routes requests to S3 and routes responses back to the VPC.
* You can limit access to your bucket from a specific Amazon VPC Endpoint or a set of endpoints using Amazon S3 bucket policies.
* Amazon Macie is an AI-powered security service that helps you prevent data loss by automatically discovering, classifying, and protecting sensitive data stored in Amazon S3. You can use Amazon Macie to protect against security threats by continuously monitoring your data and account credentials.

## Durability & Data Protection

* For S3 data, that best practice includes secure access permissions, Cross-Region Replication, versioning, and a functioning, regularly tested backup. 
* Amazon S3 uses a combination of Content-MD5 checksums and cyclic redundancy checks (CRCs) to detect data corruption. Amazon S3 performs these checksums on data at rest and repairs any corruption using redundant data.
* Once you enable Versioning for a bucket, Amazon S3 preserves existing objects anytime you perform a PUT, POST, COPY, or DELETE operation on them. By default, GET requests will retrieve the most recently written version. 
* You can use Lifecycle rules along with Versioning to implement a rollback window for your Amazon S3 objects.
* Versioning’s Multi-Factor Authentication (MFA) Delete capability can be used to provide an additional layer of security. 

## S3 Standard-Infrequent Access (S3 Standard-IA)

* S3 Standard-IA is ideal for data that is accessed less frequently, but requires rapid access when needed.
* S3 Standard-IA is designed for the same 99.999999999% durability as the S3 Standard and Amazon Glacier storage classes.
* There are two ways to get data into S3 Standard-IA:
	* directly PUT into S3 Standard-IA,
	* set Lifecycle policies to transition. 
* S3 Standard-IA is designed for long-lived but infrequently accessed data that is retained for months or years.
* S3 Standard-IA is designed for larger objects and has a minimum object storage charge of 128KB.

## S3 One Zone-Infrequent Access (S3 One Zone-IA)

* S3 One Zone-IA storage class is an Amazon S3 storage class that customers can choose to store objects in a single availability zone.
* Customers can use S3 One Zone-IA for infrequently-accessed storage, like backup copies, disaster recovery copies, or other easily re-creatable data.
* Amazon EC2 provides you the ability to pick the AZ to place resources, such as compute instances, within a region. When you use S3 One Zone-IA, S3 One Zone-IA assigns an AWS Availability Zone in the region according to available capacity.
* You can have a bucket that has different objects stored in S3 Standard, S3 Standard-IA and S3 One Zone-IA.

## Amazon Glacier

* Amazon S3 objects that are stored using the Amazon Glacier storage class are only accessible through the Amazon S3 APIs or the Amazon S3 Management Console, not Amazon Glacier APIs.
* The retrieval request of the objects archived in Glacier creates a temporary copy of your data in the S3 RRS or S3 Standard-IA storage class while leaving the archived data intact in Amazon Glacier.
* The access time of your request depends on the retrieval option you choose: Expedited, Standard, or Bulk retrievals. For all but the largest objects (250MB+), data accessed using Expedited retrievals are typically made available within 1-5 minutes. Objects retrieved using Standard retrievals typically complete between 3-5 hours. Bulk retrievals typically complete within 5-12 hours. 
* Objects that are archived to Amazon Glacier have a minimum of 90 days of storage.
* Amazon Glacier is designed for use cases where data is retained for months, years, or decades. Deleting data that is archived to Amazon Glacier is free if the objects being deleted have been archived in Amazon Glacier for 90 days or longer.

## Query in Place

* Amazon S3 allows customers to run sophisticated queries against data stored without the need to move data into a separate analytics platform. S3 offers multiple query in place options, including S3 Select, Amazon Athena, and Amazon Redshift Spectrum, allowing you to choose one that best fits your use case.
* S3 Select is an Amazon S3 feature that makes it easy to retrieve specific data from the contents of an object using simple SQL expressions without having to retrieve the entire object.
* Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL queries. Athena is serverless, so there is no infrastructure to setup or manage, and you can start analyzing data immediately.
* Amazon Redshift Spectrum is a feature of Amazon Redshift that enables you to run queries against exabytes of unstructured data in Amazon S3 with no loading or ETL required. When you issue a query, it goes to the Amazon Redshift SQL endpoint, which generates and optimizes a query plan.

## Event Notification

* Amazon S3 event notifications can be sent in response to actions in Amazon S3 like PUTs, POSTs, COPYs, or DELETEs. 

## Amazon S3 Transfer Acceleration

* 



	