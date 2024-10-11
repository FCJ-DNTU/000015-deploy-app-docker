+++
title = "Use ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Create ECR repository

- Search for **Amazon Elastic Container Registry**
- Select **Create**

![RDS](/images/8-push-image/8.1.1.png)

- Enter the name: **`fcj-lab-ecr`**
- Configure the settings as appropriate

![RDS](/images/8-push-image/8.1.2.png)

- Leave the encryption as default or configure it as needed
- Enable **Scan on push**
- Click **Create**

![RDS](/images/8-push-image/8.1.3.png)

- The repository creation in ECR is complete

![RDS](/images/8-push-image/8.1.4.png)

- Access the repository name, and select **View push commands** to see how to push images

![RDS](/images/8-push-image/8.1.5.png)

#### Access the EC2 instance that has already been connected via SSH

- Install **AWS CLI** using the following commands:
```
sudo apt -y update
sudo apt -y install unzip curl
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

![RDS](/images/8-push-image/8.1.6.png)

![RDS](/images/8-push-image/8.1.7.png)

- Unzip and verify the installation:
```
sudo unzip awscliv2.zip
sudo ./aws/install
aws --version
```

![RDS](/images/8-push-image/8.1.8.png)

![RDS](/images/8-push-image/8.1.9.png)

- Log in to ECR using the following sample command:

```
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
```
{{% notice note%}}
If this step fails, check if your EC2 instance has permission to access ECR. If not, grant it the necessary permissions or use aws config to log in using your AWS credentials.
{{% /notice%}}

![RDS](/images/8-push-image/8.1.10.png)

- Build the first Nginx image:

```
ls
cd nginx/
sudo docker build -t fcj-nginx .
```

![RDS](/images/8-push-image/8.1.11.png)

- Build the frontend image:

```
cd ...
cd frontend/
sudo docker build -t fcj-frontend .
```

![RDS](/images/8-push-image/8.1.12.png)

- Build the backend image:
 
```
cd ...
cd backend/
sudo docker build -t fcj-backend .
```

![RDS](/images/8-push-image/8.1.13.png)

- Verify the images were successfully built
- Tag each image so they can be pushed to ECR:
 
```
sudo docker images
sudo docker tag <image>:<tag> <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/<Repository_Name>:<Name_tag>
sudo docker images
```

![RDS](/images/8-push-image/8.1.14.png)

- Push images on **ECR repository**
```
sudo docker images
sudo docker push <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/<Repository_Name>:<Name_tag>
sudo docker images
```
{{% notice note%}}
If this step fails, try using root to optimize permissions for pushing images to ECR.
{{% /notice%}}

![RDS](/images/8-push-image/8.1.15.png)

- Check the images that have been pushed in the **ECR repository**

![RDS](/images/8-push-image/8.1.16.png)
