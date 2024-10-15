+++
title = "EC2 Instance Configuration"
date = 2024
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++

#### Configuring the EC2 Instance

In the AWS Console:

- Search for and select **EC2**

![5.1.1](/images/5-configure-ec2/5.1.1.png)

In the EC2 management interface:

- Select **Instances**
- Click on **Launch Instances**

![5.1.2](/images/5-configure-ec2/5.1.2.png)

- Name it `FCJ-Lab-my-server`

![5.1.3](/images/5-configure-ec2/5.1.3.png)

- Choose the operating system **Ubuntu**
- Amazon Machine Image (AMI) **Ubuntu Server 24.04**

![5.1.4](/images/5-configure-ec2/5.1.4.png)

- Instance type **t3.medium**
- Select **Create new key pair**

![5.1.5](/images/5-configure-ec2/5.1.5.png)

- Key pair name `FCJ-Lab-key`
- Select **Create key pair**

![5.1.6](/images/5-configure-ec2/5.1.6.png)

Scroll down to the security configuration section:

- VPC **FCJ-Lab-vpc**
- Choose **public subnet**
- Auto-assign public IP **Enable**
- Select **Select existing security group**
- Choose **FCJ-Lab-SG**

![5.1.7](/images/5-configure-ec2/5.1.7.png)

- Select **Launch Template**

![5.1.8](/images/5-configure-ec2/5.1.8.png)

#### Attach ECR Role to EC2

In the EC2 instance management interface:

- Select EC2 **FCJ-Lab-vpc**
- Choose **Action**
- Select **Security**
- Click on **Modify IAM role**

![5.1.12](/images/5-configure-ec2/5.1.12.png)

- Select the Role **CustomeRWECRRole**
- Click on **Update IAM role**

![5.1.13](/images/5-configure-ec2/5.1.13.png)
