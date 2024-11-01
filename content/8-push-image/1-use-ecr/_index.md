+++
title = "Using ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Create ECR Repository for Frontend Image

- Search for **Amazon Elastic Container Registry**
- Select **Create**

![8.1.1.png](/images/8-push-image/8.1.1.png)

We will create 2 different repositories to store Docker Images. First is to create a repository to store images for the frontend app.

- Repository name: `fcjresbar-fe`.

- Image tag mutability: select **Mutable**.

- Encryption configuration: leave it as default.

![8.1.2.png](/images/8-push-image/8.1.2.png)

- Click **Create** to create

![8.1.3.png](/images/8-push-image/8.1.3.png)

![8.1.4.png](/images/8-push-image/8.1.4.png)

#### Create ECR Repository for Backend Image

Similarly, now we will create for Backend Image

![8.1.5.png](/images/8-push-image/8.1.5.png)

With the following information:

- Repository name: `fcjresbar-be`.

- Image tag mutability: select **Mutable**.

- Encryption configuration: leave it as default.

![8.1.6.png](/images/8-push-image/8.1.6.png)

- Click **Create** to create

![8.1.7.png](/images/8-push-image/8.1.7.png)

![8.1.8.png](/images/8-push-image/8.1.8.png)

{{% notice note %}}
We need to create each repository for each different application to manage the version of Docker images more easily, especially for future CI/CD implementation.

{{% /notice %}}

#### Install AWS CLI

By default (10/15/2024), AWS CLI is not installed by default in Ubuntu.

![8.1.9.png](/images/8-push-image/8.1.9.png)

First we need to download **unzip** first.

```bash
sudo apt install unzip
```

![8.1.10.png](/images/8-push-image/8.1.10.png)

Then we will use the commands below to install AWS CLI.

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![8.1.11.png](/images/8-push-image/8.1.11.png)

![8.1.12.png](/images/8-push-image/8.1.12.png)

#### Push Frontend Image to ECR

Re-enter ECR Console

- Select `fcjresbar-fe`
- Press **View push commands**

![8.1.13.png](/images/8-push-image/8.1.13.png)

A dialog box will pop up and we can see a series of commands.

![8.1.14.png](/images/8-push-image/8.1.14.png)

Back to EC2 Instance, we need to use Root User to be able to log in to ECR with Docker.

In AWS console of Push commands for fcjresbar-fe

- Select the first command to authenticate to log in to Amazon Elastic Container Registry (ECR) from your local Docker environment. Before that, make sure you have configured **AWS Configure**

![8.1.15.png](/images/8-push-image/8.1.15.png)

{{% notice note %}}
Because when a user uses sudo to log in to ECR with Docker, the credential is saved in the HOME Dir of that user. But when you execute the push or pull command, it will see the credential in Root instead of in HOME Dir which was saved when logging in before.

{{% /notice %}}

In the previous sections, we have created Images for each application, so now we just need to re-tag them appropriately and push them to the corresponding Registry.

```bash
docker image ls
```

In the AWS console of Push commands for fcjresbar-fe

- Select the 3rd command line to perform tagging, replace the image resource names you created earlier

{{% notice note %}}
General format `<Account_ID>.dkr.ecr.<region>.amazonaws.com/<Repository_Name>:<Name_tag>`
{{% /notice %}}

![8.1.16.png](/images/8-push-image/8.1.16.png)

After creating, push the Image to ECR

In the AWS console of Push commands for fcjresbar-fe

- Select the push command

![8.1.17.png](/images/8-push-image/8.1.17.png)

#### Push Backend Image to ECR

Similarly, we will also view the push command of `fcjresbar-be`, remember to copy the login command. But logout first

![8.1.18.png](/images/8-push-image/8.1.18.png)

Log back in with the copied login command

![8.1.19.png](/images/8-push-image/8.1.19.png)

Similarly, tag the image appropriately

![8.1.20.png](/images/8-push-image/8.1.20.png)

Push the image to ECR

![8.1.21.png](/images/8-push-image/8.1.21.png)

#### Check the result

If successful, go to ECR Console, go to each repositories in turn, we can see the result here.

![8.1.22.png](/images/8-push-image/8.1.22.png) ![8.1.23.png](/images/8-push-image/8.1.23.png)
