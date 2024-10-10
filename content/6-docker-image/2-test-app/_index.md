+++
title = "Test Application"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

{{% notice note %}}
Nginx is running on Port **80** in the container. When we request the above URL, the container will route the request from port **3000** to **80**. Nginx will process and forward the request to the FrontEnd Application, and the website content will load.
{{% /notice %}}

![6.2.1](/images/6-docker-image/6.2.1.png)

Try logging in with a User account. If successful, it means our application is working correctly, and you will be redirected to the main interface.

![6.2.2](/images/6-docker-image/6.2.2.png)

![6.2.3](/images/6-docker-image/6.2.3.png)

Browse through other pages:

![6.2.4](/images/6-docker-image/6.2.4.png)

![6.2.5](/images/6-docker-image/6.2.5.png)

Thus, we have successfully deployed the application using Docker Image. In the next section, we will use another solution to deploy the application with Docker Compose. With this solution, managing containers will be easier.
