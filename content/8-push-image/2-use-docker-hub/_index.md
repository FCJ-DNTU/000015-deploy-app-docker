+++
title = "Use Docker Hub"
date = 2024
weight = 2
chapter = false
pre = "<b>8.2. </b>"
+++

#### Create a repository on Docker Hub

- Go to **Docker Hub** and create a repository there
- Select **Create repository**

![RDS](/images/8-push-image/8.2.1.png)

- Choose your **Namespace**
- Enter the repository name: **`fcj-lab-docker`**
- Add a description: **`Store images`**
- Select public
- Review and click **Create**

![RDS](/images/8-push-image/8.2.2.png)

- The repository on **Docker Hub** is now created

![RDS](/images/8-push-image/8.2.3.png)

#### Vào lại EC2 instance đã được ssh sẵn

- Return to **EC2**
- Log in to **Docker**
```
sudo docker login
```

![RDS](/images/8-push-image/8.2.4.png)

- Tag the images:

```
sudo docker images
sudo docker tag <Image>:<Tag> <Account_name>/<Repository_name>:<Tag_Name>
sudo docker images
```

![RDS](/images/8-push-image/8.2.5.png)

- Push the images to **Docker hub**
```
sudo docker images
sudo docker push <Account_name>/<Repository_name>:<Tag_Name>
```

![RDS](/images/8-push-image/8.2.6.png)

- Verify the images have been pushed to **Docker Hub**

![RDS](/images/8-push-image/8.2.7.png)
