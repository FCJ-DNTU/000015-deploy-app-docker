+++
title = "Deploying the Application"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Deployment with Docker Compose

We have already cloned the project from the previous sections. Navigate to **aws-fcj-container-app/docker-compose-env**.

![Image](/images/7-docker-compose/1-deploy/7.1.png?featherlight=false&width=90pc)

In this directory, we will edit the **backend.app.env** file to modify the environment for the backend.

![Image](/images/7-docker-compose/1-deploy/7.2.png?featherlight=false&width=90pc)

Proceed to change the **DB_HOST** variable to match the **RDS** we created in the previous section. Then save the file.

![Image](/images/7-docker-compose/1-deploy/7.3.png?featherlight=false&width=90pc)

In the **aws-fcj-container-app** directory, we will build the images for backend, frontend, and nginx.

![Image](/images/7-docker-compose/1-deploy/7.4.png?featherlight=false&width=90pc)

Successfully build the images.

![Image](/images/7-docker-compose/1-deploy/7.5.png?featherlight=false&width=90pc)