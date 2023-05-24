---
layout: default
title: About
nav_order: 2
---



 <h1>introduction</h1>
 
What is EC2 Spot Instance
Spot Instances are an unused part of Amazon EC2, using which you can save up to 90% on cost as compared to On-Demand cost, but AWS can interrupt your spot instances if the Current Price is higher than the Maximum Price you specified.
Spot uses the same EC2 instances (AMI and instance type) what On-Demand and Reserved Instances use. It is the best to fit for use cases where data is reproducible and can sustain the interruption at any point in time.
You can use Spot Instance as additional compute capacity to your On-Demand or Reserved Instances, where fault-tolerant is acceptable.
EC2 Spot Instances can be launched the same way you launch EC2 Instance, like using Spot Fleet. Auto Scaling Groups or AWS Management Console.
If AWS terminates or stops your Amazon EC2 Spot Instance within an hour then you will not be charged.
However, if you choose to stop or terminate your newly launched Spot Instances by yourself, you will have to pay for the total number of seconds you have used.

