+++
title = "Deploying the Application"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Deployment with Docker Compose

Before deploying with Docker Compose, we need to stop the two Docker Containers that we ran earlier (using Ctrl + C).

![7.1.1.png](/images/7-docker-compose/7.1.1.png)

![7.1.2.png](/images/7-docker-compose/7.1.2.png)

Create a new SSH session, then navigate to the `docker-compose-env` directory at the root of the project and update the `DB_HOST` variable.

![7.1.3.png](/images/7-docker-compose/7.1.3.png)

![7.1.4.png](/images/7-docker-compose/7.1.4.png)

Next, we can simply run:

```bash
cd ..
sudo docker compose -f docker-compose.app.yml up
```

This will start the two containers just like we did in the previous section.

![7.1.5.png](/images/7-docker-compose/7.1.5.png)

![7.1.6.png](/images/7-docker-compose/7.1.6.png)

Okay, it looks like our application is up and running. In the next step, we will proceed to check the application.
