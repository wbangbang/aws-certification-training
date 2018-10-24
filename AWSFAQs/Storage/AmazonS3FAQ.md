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

	