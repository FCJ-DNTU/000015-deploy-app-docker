+++
title = "Cấu hình Security Group"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Cấu hình Security Group cho EC2

Ở giao diện quản lý EC2, mục lựa chọn bên trái.

- Chọn **Security Groups**
- Chọn **Create security group**

![3.2.1](/images/3-preparation/3.2.1.png)

Cấu hình cho Security Group

- Ở phần Basic details
  - Security group name `FCJ-Lab-sg-public`
  - Description `Security group for FCJ Lab`
  - VPC **FCJ-Lab-vpc**

![3.2.2](/images/3-preparation/3.2.2.png)

- Ở phần Inbound rules chúng ta sẽ thêm những rule như sau:
  - Type **SSH** source **Anywhere-IPv4**
  - Type **HTTP** source **Anywhere-IPv4**
  - Type **HTTPS** source **Anywhere-IPv4**
  - Type **Custom TCP**, port range **3000**, source **Anywhere-IPv4**

![3.2.3](/images/3-preparation/3.2.3.png)

- Ở phần Outbound chúng ta sẽ để mặc định
- Nhấn **Create security group**

#### Cấu hình Security Group cho database instance

Tưởng tự như bước tạo security group cho EC2

- Chọn **Security Groups**
- Chọn **Create security group**

![3.2.1](/images/3-preparation/3.2.1.png)

Cấu hình cho Security Group

- Ở phần Basic details
  - Security group name `FCJ-Lab-sg-db`
  - Description `Security group for RDS database instance`
  - VPC **FCJ-Lab-vpc**

![3.2.5](/images/3-preparation/3.2.5.png)

- Ở phần Inbound
  - Chọn Type **MYSQL/Aurora**
  - Source chọn **FCJ-Lab-sg**

![3.2.6](/images/3-preparation/3.2.6.png)

- Ở phần Outbound

  - Chúng ta để mặc định

- Chọn **Create security group**

![3.2.7](/images/3-preparation/3.2.7.png)
