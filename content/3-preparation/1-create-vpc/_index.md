+++
title = "VPC Configuration"
date = 2024
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

### VPC Configuration

In the AWS console interface, perform the following:

- Search for and select **VPC**

![3.1.1](/images/3-preparation/3.1.1.png)

In the **VPC** management interface:

- Select **Your VPC**
- Click on **Create VPC**

![3.1.2](/images/3-preparation/3.1.2.png)

The VPC configuration panel appears:

- Choose **VPC and more**
- Name it `FCJ-Lab`

![3.1.3](/images/3-preparation/3.1.3.png)

In the VPC endpoint section:

- Select **None**
- Click on **Create VPC**

![3.1.4](/images/3-preparation/3.1.4.png)

After creating the VPC, we will check the information of the newly created VPC:

- Select **FCJ-Lab-vpc**

![3.1.5](/images/3-preparation/3.1.5.png)

View the overview of the VPC configuration:

![3.1.6](/images/3-preparation/3.1.6.png)

### Public Subnet Configuration

In the VPC management interface, scroll down in the left sidebar:

- Select **Subnet**
- Search for **FCJ-Lab**

![3.1.7](/images/3-preparation/3.1.7.png)

You will see two subnets: **FCJ-Lab-subnet-public-1a** and **FCJ-Lab-subnet-public-1b**.

First, we will configure **FCJ-Lab-subnet-public-1a**:

- Select **FCJ-Lab-subnet-public-1a**
- Click on **Action**
- Choose **Edit subnet settings**

![3.1.8](/images/3-preparation/3.1.8.png)

The public subnet configuration panel appears:

- Check **Enable auto-assign public IPv4 address**
- Click **Save**

![3.1.9](/images/3-preparation/3.1.9.png)

Similarly, we will configure **FCJ-Lab-subnet-public-1b**:

- Select **FCJ-Lab-subnet-public-1b**
- Click on **Action**
- Choose **Edit subnet settings**

![3.1.10](/images/3-preparation/3.1.10.png)

- Check **Enable auto-assign public IPv4 address**
- Click **Save**

![3.1.11](/images/3-preparation/3.1.11.png)

Thus, we have configured the VPC and enabled public IPv4 for the public subnets.
