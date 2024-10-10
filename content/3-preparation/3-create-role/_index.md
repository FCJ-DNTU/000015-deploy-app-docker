+++
title = "Create IAM Roles for ECR Access"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

#### Policy Configuration

In the AWS Console interface:

- Search for and select `IAM`

![3.3.1](/images/3-preparation/3.3.1.png)

In the right selection menu:

- Select **Policy**
- Click on **Create Policy**

![3.3.2](/images/3-preparation/3.3.2.png)

In the Policy Editor:

- Search for and select **Elastic Container Registry**
- Click **Next**

![3.3.3](/images/3-preparation/3.3.3.png)

A rule selection panel appears:

- In the **List** section:
  - Select **DescribeImage**
  - Select **ListImages**
- In the **Read** section:
  - Select **BatchGetImage**
  - Select **DescribeRegistry**
  - Select **DescribeRepositories**
  - Select **GetAccountSetting**
  - Select **GetAuthorizationToken**

![3.3.4](/images/3-preparation/3.3.4.png)

- In the **Resources** section:
  - Select **Specific**
  - Select **Any in this account**
  - Click **Next**

![3.3.5](/images/3-preparation/3.3.5.png)

In the Policy details section:

- Policy name: `ReadECRRepositoryContent`
- Description: `Allow pull images, describe repositories`

![3.3.6](/images/3-preparation/3.3.6.png)

- Click **Create policy**

![3.3.7](/images/3-preparation/3.3.7.png)

Similarly, we will create an additional policy for writing to ECR:

- Click **Create Policy**

A rule selection panel appears:

- In the **Read** section:
  - Select **BatchCheckLayerAvailability**
  - Select **GetAuthorizationToken**
- In the **Write** section:
  - Select **CompleteLayerUpload**
  - Select **InitialLayerUpload**
  - Select **PutImage**
  - Select **UploadLayerPart**

![3.3.8](/images/3-preparation/3.3.8.png)

- In the **Resources** section:
  - Select **Any in this account**
  - Click **Next**

![3.3.9](/images/3-preparation/3.3.9.png)

The Policy details panel appears:

- Policy name: `WriteECRRepositoryContent`
- Description: `Allow push and delete images`

![3.3.10](/images/3-preparation/3.3.10.png)

- Click **Create policy**

![3.3.11](/images/3-preparation/3.3.11.png)

#### Create Role for ECR

In the EC2 management interface:

- Select **Roles**
- Click on **Create role**

![3.3.12](/images/3-preparation/3.3.12.png)

- Select **AWS service**
- Choose **EC2**

![3.3.13](/images/3-preparation/3.3.13.png)

- Click **Next**

![3.3.14](/images/3-preparation/3.3.14.png)

- Filter by Type: **Customer managed**
- Select the two policies we just created
- Click **Next**

![3.3.15](/images/3-preparation/3.3.15.png)

In the Role details section:

- Role name: `CustomRWECRRole`
- Description: `Custom Read and Write role for ECS`

![3.3.16](/images/3-preparation/3.3.16.png)

- Click **Create role**

![3.3.17](/images/3-preparation/3.3.17.png)
