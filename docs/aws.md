---
layout: default
title: AWS
nav_order: 2
---
# AWS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
##  Day 01 - Intro to aws<br>

### Day-1_AWS_Assignment 

			Day-1_AWS_Assignment 
			(AWS Regions and EC2)

1.	What is AWS? When was AWS started and who owns it?
2.	What are some of the AWS services. Describe any five of them? 
3.	What is AWS Region, Availability Zone? What is number of AWS Regions and Availability zones as of Mar-2023?
4.	What are AWS key-pairs? 
5.	What are the pricing models for EC2instances? 
6.	What are the different types of instances? 
7.	What are reserved instances? 
8.	What is an AMI? 
9.	What is Public/Private and EIP? 
10.	What is Instance Meta data, Instance user data?

### Day 01 Assignments solutions

### Day 01 NOTES
Cloud Computing-
 - delivery of computing services by creating virtual servers over internet.

DataCenter -
Ex: Airtel.
At a time, millions of calls.
to do all those of jobs to connect, disconnect calls, data services you need of computing.

After Cloud Computing came in, companies need not maintain data center. AWS, Azure, Google Cloud Platform (GCP) run these data centers, which are given as a service to Companies like Airtel, OLA, Swiggy. 

Cloud Providers -

AWS (Amzon Web Services)
Azure (Microsoft)
GCP (Google)

Private DataCenter -
Security - Banks.
They want to move, not moved yet.

---------------------------------
Iaas - Infra as a service
Paas - Platform as a service
Saas - Software as a service

Ex - Email service (gmail)

to host a gmail service- servers, storage, network
Gmail - Saas (providing software)
AWS, Azure or GCP - Iaas (providing infra)
IBM Bluemix - Paas (.NET platform)

--------------------------------
Region and Availability Zone

31 Regions, 99 AZs.

Regions - Mumbai and Hyderabad
for Disaster Recovery purpose.
Mumbai -3 different locaitons. we call them Availbility Zones.
Mumbai -ap-south-1a, ap-south-1b-ap-south-1c
Min 2 Azs and max upto 6Azs.

How many Az's does Hyderbad(ap-south-2) have -3
How many AZ's does North Virginia(us-east-1) have -6 

--------------------------------
Amazon Web Services

Established - 2006
highly reliable, scalable and low cost infra in the cloud.

Iaas - Infra as a service. Ex: AWS, Azure, GCP
They give compute, memory and storage. you use this to create an instance and deploy you webapp.

Paas - Platform as a service
Ex: SalesForce, SAP 

Saas - Software as a service
Ex: Gmail, Dropbox
Gmail - 
you are not spinning up infra
you are not installing any email software

Benefits of Cloud Computing-
1. Low Cost - 10/- rs per hour. i'll give a system with cpu, memory and storage.
Laptop - 40-50k rupees

2. Elasticity and Agility - 
Ex: OLA. 
normal time - 100%
peak 9-11am or 6-8pm - 140%
non-peak 10pm-5am. 40% capacity

3. Open and Flexible
Ex: Operating System licensing issues.

4. Secure
Ex: Same security for everyone using.

5. Global Reach
within minutes i can deploy it globally.


Ref -
[https://aws.amazon.com/marketplace](https://aws.amazon.com/marketplace)<br>
[https://aws.amazon.com/free](https://aws.amazon.com/free)<br><br>
##  Day 02 - AWS EC2, VPC<br>

To create a virtual or Physical machine-
1. Storage			- EBS
2. Memory (or RAM)		- Memory
3. Compute (or Processor)	- vCPU
4. Operating System		- AMI
6. Networking			- VPC, Subnet and 
				Security Groups.

General Purpose - m5 series
Compute Optimized - c5 series
Memory Optimized - r5 series

m5.4x => 16 vCPU, 64GB RAM
c5 => 16 vCPU, 32 GB RAM
r5 => 16 vCPU, 128 GB RAM

EC2 instance-
CPU -1, RAM-2 GB, Operating System- Linux, Storage - 8GB 

VPC -> Create VPC(training0304) with CIDR 10.0.0.0/24
Subnets -> Empty
Internet Gateway -> Create new internet gateway(igw)
Attach to our new VPC (training0304)
Subnet -> Created Public-Subnet 
Route Tables -> Create training0304-public-route
Edit Route (0.0.0.0) to have internet gateway
Edit Subnet association to have our public subnet

Edit Subnet to have Enable auto-assign public IPv4 address checked.

Create EC2-
name for instance
Amazon Linux
Instance type - t2.micro
Keypaid - create and download ppk file
Network 
  - Select VPC and Subnet we created
  - Auto assign Public IP - Enable
  - Create Security Group. Allow Port 22-anywhere
Storage 
  - 8GB
****You should get Success (i-0e20, instance id)****
Connected to EC2 instance using Putty and ppk file.
Log-in using ec2-user as the username
13.233.199.64 (Public-ip), 10.0.0.59 (Private-ip)
3.109.202.144 (new public-ip), private-ip remains same


Elastic Ip -

Allocate a new EIP (13.233.45.109)
Associate Elastic Ip
Instance (i-0e20xx)
### Connect using putty using Elastic-IP
Clean-up

Goto Storage -> Under Bloc devices - if Delete on Termination set to Yes.
Goto Instance State-> Terminate Instance. Wait for state to change to Terminated.

Release the Elastic IP back to Amazon IP pool.
Elastic IP addresses released.


OS - Amazon Linux, t3-small $0.0208
OS - Windows, t3.small $0.0392
OS - RHEL, t3.small - $0.0808

Region, AZ
Steps -
1. Select Region
2. Create VPC, Subnets (Public Private, Private Subnet)
3. Launch VM with a specfic config

VPC CIDR - 172.0.10.0/24 - (32-24 = 8, 2^8 = 256 IPs)
public subnets CIDR - 172.0.10.0/25 (2^7, 128 IPs in each)
private subnet CIDR - 172.0.10.128/25

Route tables -
Private Route - no change
Public Route (we connected igw)

public ip -  3.111.47.72 - ip changes on every reboot
private ip - 172.0.10.171 - constant

### Elastic IP - 13.200.42.3
OLA, Swiggy
Computer capacity - 1000 servers (on-demand capacity)
Peak Period - +500 servers (Spot capacity)
non peak -	-500 (24*7 - Resvere)

10000 servers
4000 - resvered -
5000 - ondemand
1000 - spot capacity


Reference -
Instance types:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html

https://aws.amazon.com/ec2/pricing/on-demand/


###   Day-2_AWS_Assignment 

                   Day-2_AWS_Assignment 
            (EC2 Security Groups, VPC and Subnets)

1.	What are AWS security groups?
2.	What is VPC?
3.	What is meant by subnet?
4.	What are Internet and NAT gateways?
5.	How can you convert a public subnet to private subnet?
6.	What is the difference between security groups and network access control list? 
7.	By default how many Ip address does AWS reserve in a subnet?
8.	What are route tables. What is the difference between Private Route and Public Route table.
9.	What are VPC flow logs.
10.	What is VPC peering.<br>


## Day 03 - AMI-SPOT-ASG

 ### AMI -
Create an AMI from an existing instances
its a backup of your instance. you take AMI at regular intervals.
Once instance is terminated. AMI still exists.

AMI is stored on S3. it will apply standard S3 charges.


 ### Spot Instance

OnDemand Instances - 
Reserved Instances -

Mumbai Region -> AZ
10,0000 servers

Total servers used - 9000
Reserved - 7000
OnDemand - 2000
unused capacity -1000 servers

Amazon dont want to keep it idle.
reduced price - Spot capacity -1000 servers
500 servers removed from spot.t
they put it under ondemand

Uber- 4000 servers
3000 servers - Reserved Instances 1 yr
1000 servers - OnDemand
peak period - 9-10am, 6-7pm office
500 servers - spot capacity


Zomato - 5000 serers 
4000 servers - Reserved (10pm-5am)
1000 servers - OnDemand (5am-11am)
Peak period - 31st night, everyday during breakfast/lunch/dinner time. (9am-11am)
500 servers - spot capacity - XX. they pay ondemand price for 500 servers

----------------------------
Auto-Scaling

AutoScaling - automatically increase or decrease of the compute capacity.

benefits of auto-scaling
high availability.
fault tolernace -replacing unhealthy instance with a healthy instance.
cost savings.
high performance.
FREE

lab demo.

------------------------------

Weekend Assignment -

How many ways can you create an EC2 instance

1. AWS Console.
2. Auto Scaling Group
3. CloudFormation
4. CLI Commands
5. 
6. 


















