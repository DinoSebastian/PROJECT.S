# PROJECT.S
AWS SOLUTION ARCHITECT PROJECT

Background:
A start-up company wants to host its Python and React-based application (Backend: Python API and Frontend React) using AWS. But they are not familiar with the AWS cloud platform. They want to ensure that the application is secure, scalable, highly available, and cost-efficient. As a solutions architect, you have to design a proper solution to meet their below requirements.

Goal:
To architect a solution that is secure, scalable, highly available, and cost-effective using AWS.

Requirements:
➢They are concerned about the security of the application, so they have decided to isolate their network from the rest of the customers virtually. Set-up a secure virtual network where the only frontend of application is accessible by users and not the database
➢Execute the React application code using AWS Elastic Beanstalk. Ensure that the source code of Web application is automatically picked, pushed to the master branch, and deployed on the servers
➢Ensure all the UI images served to the frontend application code are provisioned via a secure storage unit
➢There should be enough backups for both the Web and Database server, so if the set-up crashes, we can launch a new one from the disaster recovery backups
➢They are uncertain about the traffic pattern that how low or high it can be, so they want the Web application to be running on at least two EC2 instances all time, and when there is a high load, they must burst up to four instances in total
➢The Web application should be highly available, even if any VM fails to respond to queries, there should be a mechanism to switch the connection to another healthy VM automatically
➢Automate the download all the activity logs into a CSV file, create a stream of data, analyze it, and display it via a dashboard
➢The Web application should also be cached globally, so users worldwide can access it with low latency


Solution:
Based on the requirements you provided, here is a proposed solution design:

1.Security and Isolation

1.	Create a Virtual Private Cloud (VPC) in AWS with private and public subnets.
2.	Place the database in the private subnet that is not accessible from the internet.
3.	Place the frontend application in the public subnet that is accessible from the internet.
4.	Use security groups to control inbound and outbound traffic to the application and database.
5.	Use Network Access Control Lists (NACLs) to control traffic between the subnets

2.React Application Deployment

1.	Use AWS Elastic Beanstalk to deploy the React application.
2.	Set up an automatic deployment pipeline to pick up the source code from the master branch and deploy it on the Elastic Beanstalk environment.
3.	Use AWS CodePipeline and CodeBuild to automate the build and deployment process.

3.Secure Storage for UI Images

1.	Use Amazon S3 to provision a secure storage unit for UI images.
2.	Enable encryption at rest and in transit for S3 objects.
3.	Use IAM roles to control access to S3 buckets and objects.

4.Disaster Recovery and Backups

1.	Use AWS CloudFormation to create and manage stacks of AWS resources, including EC2 instances and databases.
2.	Set up automated backups using AWS Backup for both the web and database servers.
3.	Test the disaster recovery process regularly to ensure backups are working and can be used to launch new instances.

5.Elastic Scaling and High Availability

1.	Use Amazon EC2 Auto Scaling to automatically adjust the number of EC2 instances based on traffic patterns.
2.	Set up a minimum of two EC2 instances to ensure high availability and automatically scale up to four instances during high traffic.
3.	Use Elastic Load Balancing to distribute traffic across multiple EC2 instances and ensure high availability.
4.	Use Route 53 to provide global DNS resolution and failover between regions.

6.Activity Logs and Dashboard

1.	Use AWS CloudTrail to record activity logs for the application and store them in Amazon S3.
2.	Use AWS Glue to extract, transform and load the logs data into Amazon Redshift.
3.	Use Amazon QuickSight to analyse the data and create dashboards and visualizations.

7.Global Caching

1.	Use Amazon CloudFront to cache and distribute the web application content globally.
2.	Use Route 53 to create a latency-based routing policy that directs users to the nearest CloudFront edge location for improved performance.

This proposed solution design meets the project requirements by providing a secure, scalable, highly available, and cost-effective architecture using AWS services.

