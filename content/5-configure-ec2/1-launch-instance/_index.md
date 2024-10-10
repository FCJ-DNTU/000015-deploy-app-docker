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

#### Install Libraries and Application on EC2

In this step, we need to SSH into the EC2 instance using the Command Line, Visual Studio Code CLI, or any other tool of your choice.

- Clone the GitHub repository

```bash
https://github.com/AWS-First-Cloud-Journey/aws-fcj-container-app.git
```

![5.1.10](/images/5-configure-ec2/5.1.10.png)

- Install Docker compose

```bash
#!/bin/bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update -y
sudo apt install docker-ce -y
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker -v
docker-compose -v
```

![5.1.11](/images/5-configure-ec2/5.1.11.png)

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
