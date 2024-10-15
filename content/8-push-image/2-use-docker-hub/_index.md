+++
title = "Use Docker Hub"
date = 2024
weight = 2
chapter = false
pre = "<b>8.2. </b>"
+++

#### Create a repository on Docker Hub

- Go to **Docker Hub**, which has been prepared, and create a repository there.
- Select **Create repository**

![8.2.1.png](/images/8-push-image/8.2.1.png)

- Choose the **Namespace** as your account.
- Enter the repository name: `fcjresbar-fe`
- Enter the description: `Frontend Image of FCJ Resbar`
- Select public
- Review and select **Create**

![8.2.2.png](/images/8-push-image/8.2.2.png)

- Successfully created a **repository** on **Docker Hub**.

![8.2.3.png](/images/8-push-image/8.2.3.png)

Similarly, create a repository for the backend image.

- Choose the **Namespace** as your account.
- Enter the repository name: `fcjresbar-be`.
- Enter the description: `Backend Image of FCJ Resbar`.
- Select public.
- Review and select **Create**.

![8.2.4.png](/images/8-push-image/8.2.4.png)

Results:

![8.2.5.png](/images/8-push-image/8.2.5.png)

#### Push frontend image to Docker Hub

Now we are ready to push the images to their respective repositories.

Logout and log in to Docker Hub. Make sure to log in with the correct account and password that you used to create the repositories in the previous step.

![8.2.6.png](/images/8-push-image/8.2.6.png)

Change the tag for the frontend image.

![8.2.7.png](/images/8-push-image/8.2.7.png)

Push the frontend image to Docker Hub.

![8.2.8.png](/images/8-push-image/8.2.8.png)

#### Push backend image to Docker Hub

Similarly, we will quickly tag and push the backend image to Docker Hub.

![8.2.9.png](/images/8-push-image/8.2.9.png)

#### Results

After pushing, we can see that the images have been pushed to their respective repositories.

![8.2.10.png](/images/8-push-image/8.2.10.png)

![8.2.11.png](/images/8-push-image/8.2.11.png)
