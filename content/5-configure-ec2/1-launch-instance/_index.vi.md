+++
title = "Cấu hình EC2 Instance"
date = 2024
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++

#### Cấu hình cho EC2 Instance

Ở giao diện AWS Console

- Tìm kiếm và chọn **EC2**

![5.1.1](/images/5-configure-ec2/5.1.1.png)

Ở giao diện quản lý EC2

- Chọn **Instance**
- Chọn **Launch Instances**

![5.1.2](/images/5-configure-ec2/5.1.2.png)

- Name `FCJ-Lab-my-server`

![5.1.3](/images/5-configure-ec2/5.1.3.png)

- Chọn hệ điều hành **Ubuntu**
- Amazon Machine Image (AMI) **Ubuntu Server 24.04**

![5.1.4](/images/5-configure-ec2/5.1.4.png)

- Instance type **t3.medium**
- Chọn **Create new key pair**

![5.1.5](/images/5-configure-ec2/5.1.5.png)

- Key pair name `FCJ-Lab-key`
- Chọn **Create key pair**

![5.1.6](/images/5-configure-ec2/5.1.6.png)

Kéo xuống dưới phần cấu hình security

- VPC **FCJ-Lab-vpc**
- Chọn **subnet public**
- Auto-assign public IP **Enable**
- Chọn **Select existing security group**
- Chọn **FCJ-Lab-SG**

![5.1.7](/images/5-configure-ec2/5.1.7.png)

- Chọn **Launch Template**

![5.1.8](/images/5-configure-ec2/5.1.8.png)

#### Gắn Role ECR cho EC2

Ở giao diện quan lý EC2 instance

- Chọn EC2 **FCJ-Lab-vpc**
- Chọn **Action**
- Chọn **Security**
- Chọn **Modify IAM role**

![5.1.12](/images/5-configure-ec2/5.1.12.png)

- Chọn Role **CustomeRWECRRole**
- Chọn **Update IAM role**

![5.1.13](/images/5-configure-ec2/5.1.13.png)
