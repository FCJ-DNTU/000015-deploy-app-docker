+++
title = "Launch RDS Instance"
date = 2024
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

#### Create RDS Instance

- Go to the section: **Databases**
- Select: **Create Database**

![RDS](/images/4-rds/4.2.1.png)

- Choose the method: **Standard create**
- Select the database type: **MySQL**

![RDS](/images/4-rds/4.2.2.png)

- Select the template: **Dev/Test**
- Choose **Multi-AZ DB instance**

{{% notice tip%}}
This section can be adjusted according to your needs to optimize costs, but there are some limitations, so it's important to research carefully.
{{% /notice%}}

![RDS](/images/4-rds/4.2.3.png)

- Enter the DB instance name: **`fcj-lab-rds-instance`**
- Enter the  username: **`admin`**
- Enter the password: **`letmein12345`**

![RDS](/images/4-rds/4.2.4.png)

- Adjust configurations as needed

![RDS](/images/4-rds/4.2.5.png)

- Connect to the previously created **VPC**
- Select the **Subnet** created in the previous section

![RDS](/images/4-rds/4.2.6.png)

- Choose the **Security group** created for the DB
- The following sections can be left as default or configured based on your preferences

![RDS](/images/4-rds/4.2.7.png)

- Review all configurations carefully and click **Create**

![RDS](/images/4-rds/4.2.8.png)

- Complete the creation of the **DB instance**, it will take about 15 minutes to become **Available**

![RDS](/images/4-rds/4.2.9.png)

