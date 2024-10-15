+++
title = "Install required libraries"
date = 2024
weight = 2
chapter = false
pre = "<b>5.2. </b>"
+++


First, we need to connect to the EC2 instance that we just created using SSH. Then, run the following commands to update the system and its packages.

```bash
sudo apt update -y
sudo apt upgrade -y
```

![5.2.1.png](/images/5-configure-ec2/5.2.1.png)

![5.2.2.png](/images/5-configure-ec2/5.2.2.png)

#### Install Docker

Next, we need to install Docker to deploy applications later. Use the following commands to install Docker:

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

![5.2.3.png](/images/5-configure-ec2/5.2.3.png)

Then proceed to install the necessary Docker libraries.

![5.2.4.png](/images/5-configure-ec2/5.2.4.png)

#### Install MySQL Client

To add data to the RDS instance, we need to install the MySQL Client. Use the following command:

```bash
sudo apt install mysql-client
```

![5.2.5.png](/images/5-configure-ec2/5.2.5.png)

### Check the results

Docker Test

![5.2.6.png](/images/5-configure-ec2/5.2.6.png)

MySQL Client Test

![5.2.7.png](/images/5-configure-ec2/5.2.7.png)

Finally, to clone the source code, we need Git. Check if Git is installed:

![5.2.8.png](/images/5-configure-ec2/5.2.8.png)

Everything is now set up correctly.

### Clone the Project from GitHub

Before proceeding to the next steps, we need to clone the project source code.

```bash
git clone https://github.com/AWS-First-Cloud-Journey/aws-fcj-container-app.git
```

![5.2.9.png](/images/5-configure-ec2/5.2.9.png)
