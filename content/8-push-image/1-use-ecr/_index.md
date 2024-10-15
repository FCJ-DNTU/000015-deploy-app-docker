+++
title = "Use ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Create ECR Repository for Frontend Image

- Search for **Amazon Elastic Container Registry**
- Select **Create**

![8.1.1.png](/images/8-push-image/8.1.1.png)

We will create two different repositories to hold the Docker Images. First, we will create a repository to store the image for the frontend app.

- Repository name: `fcjresbar-fe`.
- Image tag mutability: select **Mutable**.
- Encryption configuration: leave it as default.

![8.1.2.png](/images/8-push-image/8.1.2.png)

- Click **Create** to create the repository.

![8.1.3.png](/images/8-push-image/8.1.3.png)

![8.1.4.png](/images/8-push-image/8.1.4.png)

#### Create ECR Repository for Backend Image

Similarly, we will now create a repository for the Backend Image.

![8.1.5.png](/images/8-push-image/8.1.5.png)

With the following information:

- Repository name: `fcjresbar-be`.
- Image tag mutability: select **Mutable**.
- Encryption configuration: leave it as default.

![8.1.6.png](/images/8-push-image/8.1.6.png)

- Click **Create** to create the repository.

![8.1.7.png](/images/8-push-image/8.1.7.png)

![8.1.8.png](/images/8-push-image/8.1.8.png)

{{% notice note %}}
 We need to create a separate repository for each application to manage the versions of Docker images more easily, especially for performing CI/CD later on.

{{% /notice %}}

#### Install AWS CLI

By default (as of October 15, 2024), AWS CLI is not pre-installed in Ubuntu.

![8.1.9.png](/images/8-push-image/8.1.9.png)

First, we need to install **unzip**.

![8.1.10.png](/images/8-push-image/8.1.10.png)

Then, we will use the commands below to install the AWS CLI.

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![8.1.11.png](/images/8-push-image/8.1.11.png)

![8.1.12.png](/images/8-push-image/8.1.12.png)

#### Push Frontend Image to ECR

Vào lại ECR Console

- Select `fcjresbar-fe`
- Click **View push commands**

![8.1.13.png](/images/8-push-image/8.1.13.png)

A dialog box will pop up, and we can see a series of commands.

![8.1.14.png](/images/8-push-image/8.1.14.png)

Return to the EC2 Instance; we need to use the Root User to log in to ECR with Docker.

![8.1.15.png](/images/8-push-image/8.1.15.png)

{{% notice note %}}
When using sudo to log in to ECR with Docker, the credentials are stored in that user's HOME directory. However, when performing push or pull commands, it will look for credentials in the Root directory instead of the stored HOME directory.
{{% /notice %}}

In the previous sections, we created the Images for each application, so now we just need to tag them appropriately and push them to the corresponding Registries.

![8.1.16.png](/images/8-push-image/8.1.16.png)

{{% notice note %}}
General format `<Account_ID>.dkr.ecr.<region>.amazonaws.com/<Repository_Name>:<Name_tag>`
{{% /notice %}}

After creating the tag, proceed to push the Image to ECR.

![8.1.17.png](/images/8-push-image/8.1.17.png)

#### Push Backend Image to ECR

Similarly, we will view the push command for `fcjresbar-be`, remembering to copy the login command. But log out first.

![8.1.18.png](/images/8-push-image/8.1.18.png)

Log in again using the copied login command.

![8.1.19.png](/images/8-push-image/8.1.19.png)

Again, tag the image appropriately.

![8.1.20.png](/images/8-push-image/8.1.20.png)

Push the image to ECR.

![8.1.21.png](/images/8-push-image/8.1.21.png)

#### Check the Results

If successful, go into the ECR Console and navigate to each repository to see the results.

![8.1.22.png](/images/8-push-image/8.1.22.png)

![8.1.23.png](/images/8-push-image/8.1.23.png)
