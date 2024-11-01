+++
title = "Deploy Application"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

In the previous section, **2 Deploy on Local**, we manually deployed the following:

- Database Server
- Web Server
- End User Application

As mentioned before, there were several limitations in this approach. Now, we'll deploy the infrastructure on the cloud using Docker, eliminating the need to download and install everything manually. If you're familiar with Docker basics (especially networking), this part will not be too challenging.

In the earlier 4 Configure RDS step, we already configured the Database Server using Amazon RDS, so we no longer need to worry much about maintenance, access security, or data safety. Now, in this cloud deployment, we'll focus on deploying the remaining applications using Docker Images.

Next, we'll deploy using Docker Compose so you can see the difference between deploying on Local, deploying with Docker Images on the Cloud, and deploying with Docker Compose on the Cloud.

{{% notice note %}}
In the 2 Deploy on Local section, you can consider this as deploying in a development environment, but now we'll deploy in a production or testing environment.
{{% /notice %}}

#### Deploy the Web Server

Go to the source code directory we cloned earlier, `aws-fcj-container-app`. Inside the `backend` folder, modify the contents of the `.env` file, specifically changing the `DB_HOST` variable.

![6.1.1.png](/images/6-docker-image/6.1.1.png)

![6.1.2.png](/images/6-docker-image/6.1.2.png)

Now the web server is ready to run. Next, run the command below:

```bash
sudo docker build . -t backend-image
```

![6.1.3.png](/images/6-docker-image/6.1.3.png)

Before starting the web server container, we need to create a **network** for the containers to communicate with each other:

```bash
sudo docker network create my-network
```

Then, run the Docker container using the newly built Docker Image:

```bash
sudo docker run -p 5000:5000 --network my-network --name backend backend-image
```

![6.1.4.png](/images/6-docker-image/6.1.4.png)

#### Deploy the Application

Now, open a new SSH session to follow the same steps, but this time, we'll deploy the Application.

![6.1.5.png](/images/6-docker-image/6.1.5.png)

- `cd` into the `frontend` folder.
- Run the command below:

```bash
sudo docker build . -t frontend-image
```

![6.1.6.png](/images/6-docker-image/6.1.6.png)

Then, run the Docker container using the newly created Docker Image:

```bash
sudo docker run -p 3000:80 --network my-network --name frontend frontend-image
```

![6.1.7.png](/images/6-docker-image/6.1.7.png)
