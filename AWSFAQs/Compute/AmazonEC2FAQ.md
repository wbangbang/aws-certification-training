# Amazon EC2 FAQs

Source: https://aws.amazon.com/ec2/faqs/

## General

* When you launch your Amazon EC2 instances you have the ability to store your root device data on Amazon EBS or the local instance store. 
	* By using Amazon EBS, data on the root device will persist independently from the lifetime of the instance. 
	* The local instance store only persists during the life of the instance. 
* An Amazon Machine Image (AMI) is simply a packaged-up environment that includes all the necessary bits to set up and boot your instance. Your AMIs are your unit of deployment. You might have just one AMI or you might compose your system out of several building block AMIs (e.g., webservers, appservers, and databases).
* You are limited to running up to a total of 20 On-Demand instances across the instance family, purchasing 20 Reserved Instances, and requesting Spot Instances per your dynamic Spot limit per region. 
	