Background:

You are recently promoted from a Cloud Engineer to a Cloud Architect and assigned a project to prepare a new environment in the cloud, to which your team will later migrate their applications

Goal:

To architect a solution that is secure, scalable, highly available, and cost effective using AWS


Requirements:

•	They are concerned about the security of the environment, so they have decided to virtually isolate their network from the rest of the customers and the rest of the environments in the same AWS Cloud Account

•	Due to the budget issue, the company cannot afford a dedicated DB engineer, so they are willing to outsource the DB management from a Cloud provider, to store and maintain the customer information received by PHP application. You must pick the right solution from AWS, which should be a Platform as a Service. It should also Provide high availability, patching, and back ups. (hint: Create DB subnet group)

•	And about disaster recovery, you should have enough backups for both the Web and Database server, so if in case the environment crashes, we can launch a new environment from the disaster recovery backups

•	Design a dynamic website where the customers can enter their details, which should be stored in a database

•	They are uncertain about the traffic pattern that how low or high it can be, so they have a requirement that the environment should be running at least two EC2 servers all time, and when there is a high load, they must burst up to four servers in total

•	Now the company cannot afford a dedicated engineer for monitoring, so you must automate the incident management through an event notification. Anytime there is an increase and decrease in the VM’s due to high or low traffic, you must receive a notification via email

•	The application should be highly available, even if a VM fails to respond to queries, there should be a mechanism to shift the connection to another healthy VM automatically

•	Your Dynamic Website should also be cached globally, so users worldwide can access it with less latency. The customer is okay if we get an unfriendly AWS generated URL for accessing the website




SOLUTION

Based on the requirements you provided, here is an AWS architecture solution that addresses the customer's needs:

1.Network Isolation: 

Create a Virtual Private Cloud (VPC) with public and private subnets. Place the web server in the public subnet and the database server in the private subnet. Configure security groups to allow access to the web server from the Internet and access to the database server from the web server only.

2.Database: 

Use Amazon Relational Database Service (RDS) for MySQL to manage the database. Create a DB subnet group with private subnets in different Availability Zones for high availability. Enable automatic backups and configure retention periods to meet the customer's needs.

3.Disaster Recovery: 

Use AWS Backup to create backup plans for both the web and database servers. Store backups in Amazon Simple Storage Service (S3) and configure cross-region replication for additional resiliency.


4.Dynamic Website: 

Build a PHP-based dynamic website and deploy it on Amazon Elastic Compute Cloud (EC2) instances. Use Elastic Load Balancing to distribute traffic across the EC2 instances.

5.Auto Scaling:

Create an Auto Scaling group with a minimum of two EC2 instances and a maximum of four instances. Configure scaling policies to automatically add or remove instances based on CPU utilization.

6.Event Notification: 

Use Amazon Simple Notification Service (SNS) to send email notifications when an instance is launched or terminated.

7.High Availability: 

Use Elastic Load Balancing to monitor the health of the EC2 instances and automatically shift traffic to healthy instances in case of failure.

8.Global Caching: 

Use Amazon CloudFront to cache the website globally and reduce latency for users worldwide. Configure CloudFront to use the website's AWS generated URL for access.






