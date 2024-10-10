+++
title = "Deploy Application"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

In the previous **2 Deploy on Local** section, we manually deployed the following:

- Database Server
- NginX Server
- Web Server
- End User Application

There were many limitations, as mentioned earlier, so now we will deploy this infrastructure on the Cloud using Docker. This means we no longer need to worry about downloading and installing. If you are familiar with the basic concepts of Docker (especially networking), this part won't be too difficult.

In step **4 Configure RDS**, we already configured the Database Server with Amazon RDS, so from a technical, maintenance, and security perspective, we won't need to worry much about access or data safety anymore. Therefore, in this cloud deployment, we will focus on deploying the remaining applications with Docker Images.

In the following sections, we will deploy with Docker Compose, allowing you to see the difference when deploying locally with Docker Images on the Cloud and with Docker Compose on the Cloud.

#### Deploying the Web Server

First, we will need the Endpoint of the RDS we created earlier.

- Go to the RDS Console.
- Select the RDS Instance you just created.
- Copy the Endpoint.

![6.1.1](/images/6-docker-image/6.1.1.png)

Source directory:

![6.1.2](/images/6-docker-image/6.1.2.png)

Navigate to the source directory that we cloned earlier, `aws-fcj-container-app`. In the `backend` folder, we will modify the `.env` file, specifically the `DB_HOST` variable.

![6.1.3](/images/6-docker-image/6.1.3.png)

![6.1.4](/images/6-docker-image/6.1.4.png)

Now our web server is ready to run. Next, execute the command below:

```bash
docker build . -t backend-image
```

![6.1.5](/images/6-docker-image/6.1.5.png)

Before starting the Container for the web server, we need to create a **network** for the containers to communicate with each other.

```bash
docker network create my-network
```

Next, run the Docker Container with the newly created Docker Image:

```bash
docker run -p 5000:5000 --network my-network --name backend backend-image
```

![6.1.7](/images/6-docker-image/6.1.7.png)

#### Deploying the Application

Now, open a new SSH Session and follow similar steps as above, but this time, we will deploy the Application.

![6.1.8](/images/6-docker-image/6.1.8.png)

- `cd` into the `frontend` directory
- Run the command below:

```bash
docker build . -t frontend-image
```

![6.1.9](/images/6-docker-image/6.1.9.png)

Next, run the Docker Container with the newly created Docker Image:

```bash
docker run --network my-network --name frontend frontend-image
```

![6.1.10](/images/6-docker-image/6.1.10.png)

#### Deploying the Nginx Server

Open another session. Before starting the Nginx Server, check if the previous containers are still running:

```bash
docker ps
```

![6.1.11](/images/6-docker-image/6.1.11.png)

Ok, everything is running as expected.

To ensure the system runs smoothly, we will add one more step: deploying the Nginx Server, which will act as a Proxy Server. Start the Nginx Server by:

- `cd` into the `nginx` directory
- Run the command below:

```bash
docker build . -t nginx-image
```

![6.1.12](/images/6-docker-image/6.1.12.png)

Next, run the Docker Container with the newly created Docker Image:

```bash
docker run -p 3000:80 --network my-network --name nginx nginx-image
```

![6.1.13](/images/6-docker-image/6.1.13.png)

Now, the application is ready for testing.
