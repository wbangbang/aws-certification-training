# Amazon EC2 FAQs

Source: https://aws.amazon.com/ec2/faqs/

## General

* When you launch your Amazon EC2 instances you have the ability to store your root device data on Amazon EBS or the local instance store. 
	* By using Amazon EBS, data on the root device will persist independently from the lifetime of the instance. 
	* The local instance store only persists during the life of the instance. 
* An Amazon Machine Image (AMI) is simply a packaged-up environment that includes all the necessary bits to set up and boot your instance. Your AMIs are your unit of deployment. You might have just one AMI or you might compose your system out of several building block AMIs (e.g., webservers, appservers, and databases).
* You are limited to running up to a total of 20 On-Demand instances across the instance family, purchasing 20 Reserved Instances, and requesting Spot Instances per your dynamic Spot limit per region. 

## Billing

* Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance. Billing ends when the instance terminates.

## Hardware Information

* Amazon EC2 instances are grouped into 5 families: General Purpose, Compute Optimized, Memory Optimized, Storage Optimized and Accelerated Computing instances.

## Elastic IP

* By default, all accounts are limited to 5 Elastic IP addresses per region.
* In order to help ensure our customers are efficiently using the Elastic IP addresses, we impose a small hourly charge for each address when it is not associated to a running instance.
* By default, every instance comes with a private IP address and an internet routable public IP address. The private IP address remains associated with the network interface when the instance is stopped and restarted, and is released when the instance is terminated. The public address is associated exclusively with the instance until it is stopped, terminated or replaced with an Elastic IP address. 

## Enhanced Networking

* For supported Amazon EC2 instances, this feature provides higher packet per second (PPS) performance, lower inter-instance latencies, and very low network jitter.
* To take advantage of Enhanced Networking you need to launch the appropriate AMI on a supported instance type in a VPC.
* Amazon VPC allows us to deliver many advanced networking features to you that are not possible in EC2-Classic. Enhanced Networking is another example of a capability enabled by Amazon VPC.

## Amazon Elastic Block Store (EBS)

* The data stored on a local instance store will persist only as long as that instance is alive. However, data that is stored on an Amazon EBS volume will persist independently of the life of the instance.
* Amazon EBS includes two major categories of storage: SSD-backed storage for transactional workloads (performance depends primarily on IOPS) and HDD-backed storage for throughput workloads (performance depends primarily on throughput, measured in MB/s). 
	* SSD-backed volumes are designed for transactional, IOPS-intensive database workloads, boot volumes, and workloads that require high IOPS. SSD-backed volumes include Provisioned IOPS SSD (io1) and General Purpose SSD (gp2). 
	* HDD-backed volumes are designed for throughput-intensive and big-data workloads, large I/O sizes, and sequential I/O patterns. HDD-backed volumes include Throughput Optimized HDD (st1) and Cold HDD (sc1). 
* While you are able to attach multiple volumes to a single instance, attaching multiple instances to one volume is not supported at this time.
* Snapshots can be done in real time while the volume is attached and in use.
* EBS offers seamless encryption of data volumes and snapshots. 

## Amazon Elastic File Storage (EFS)

* To access your file system, you mount the file system on an Amazon EC2 Linux-based instance using the standard Linux mount command and the file system’s DNS name. Once you’ve mounted, you can work with the files and directories in your file system just like you would with a local file system.
* Amazon EFS is compatible with all Amazon EC2 instance types and is accessible from Linux-based AMIs.
* Amazon EFS file systems can be mounted on an Amazon EC2 instance, so any data that is accessible to an Amazon EC2 instance can also be read and written to Amazon EFS.
* Amazon EFS supports one to thousands of Amazon EC2 instances connecting to a file system concurrently.

	