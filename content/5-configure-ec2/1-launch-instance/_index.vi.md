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

#### Cài đặt thư viện và ứng dụng vào EC2

Ở bước này, chúng ta cần thực hiện SSH tới EC2 qua Command Line hoặc, Visual Studio Code CLI, hoặc công cụ bất kỳ.

- Clone repository github

```bash
https://github.com/AWS-First-Cloud-Journey/aws-fcj-container-app.git
```

![5.1.10](/images/5-configure-ec2/5.1.10.png)

- Cài đặt Docker compose

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
