# network-monitoring-aws

## Problem 
"Our SysOps Administration team has been tasked to design and implement a network monitoring solution for our company. In the past, the company has detected malicious activities aimed at disrupting the network infrastructure at the company. We need you to devise a network monitoring solution that helps the company to meet compliance requirements, monitor key metrics and configure automated notifications in case of any suspected security event. On the network monitoring side, we want you to implement AWS VPC Flow Logs for your VPCs network interfaces.

To build a logging and notifications layer for the entire end-to-end solution, you will leverage CloudWatch filters and CloudWatch alarms to monitor AWS VPC Flow Logs that are ingested into CloudWatch Logs. We want you to report any security events via SNS notifications as soon as these are detected. You will need to build the analytics layer using Amazon Athena that analyzes the access trends for the VPC Flow Logs stored in S3."

## Solution
1. I created a VPC and a public subnet within the VPC. I provisioned an Internet Gateway and made route entries for the Internet Gateway in the main Route Table for the given VPC.
2. I created two separate VPC Flow Logs for the VPC created in task one. The first VPC Flow Log had the destination as CloudWatch Logs, which was used to create a CloudWatch alarm. The alarm is triggered when a forbidden traffic event is detected. This in turn will send an email via SNS notifications. The second VPC Flow Log had an S3 bucket as it's destination which was used for analytics leveraging Amazon Athena.
3. I created the EC2 instance in the public subnet of the VPC that was created in task one. I created a security group to allow SSH access into this instance.
4. I setup an Athena table that reads the VPC Flow Logs data from S3 to analyse the access trends for the VPC Flow Logs stored in S3.
<img width="1440" alt="solution" src="https://github.com/Adamcoakley/network-monitoring-aws/blob/main/images/solution.png">
