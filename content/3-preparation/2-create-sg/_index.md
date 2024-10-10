+++
title = "Security Group Configuration"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Security Group Configuration for EC2

In the EC2 management interface, in the left selection menu:

- Select **Security Groups**
- Click on **Create security group**

![3.2.1](/images/3-preparation/3.2.1.png)

Configure the Security Group:

- In the **Basic details** section:
  - Security group name: `FCJ-Lab-sg-public`
  - Description: `Security group for FCJ Lab`
  - VPC: **FCJ-Lab-vpc**

![3.2.2](/images/3-preparation/3.2.2.png)

- In the **Inbound rules** section, add the following rules:
  - Type: **SSH**, Source: **Anywhere-IPv4**
  - Type: **HTTP**, Source: **Anywhere-IPv4**
  - Type: **HTTPS**, Source: **Anywhere-IPv4**
  - Type: **Custom TCP**, Port range: **3000**, Source: **Anywhere-IPv4**

![3.2.3](/images/3-preparation/3.2.3.png)

- For the **Outbound rules**, we will leave it as default.
- Click on **Create security group**.

#### Security Group Configuration for Database Instance

Similar to the steps for creating a security group for EC2:

- Select **Security Groups**
- Click on **Create security group**

![3.2.1](/images/3-preparation/3.2.1.png)

Configure the Security Group:

- In the **Basic details** section:
  - Security group name: `FCJ-Lab-sg-db`
  - Description: `Security group for RDS database instance`
  - VPC: **FCJ-Lab-vpc**

![3.2.5](/images/3-preparation/3.2.5.png)

- In the **Inbound rules** section:
  - Select Type: **MYSQL/Aurora**
  - Source: Select **FCJ-Lab-sg**

![3.2.6](/images/3-preparation/3.2.6.png)

- For the **Outbound rules**:

  - Leave it as default.

- Click on **Create security group**.

![3.2.7](/images/3-preparation/3.2.7.png)
