+++
title = "Add Database for Testing"
date = 2024
weight = 3
chapter = false
pre = "<b>5.3. </b>"
+++

#### Preparation

To ensure the application works, we need to load data into the RDS instance.

We will use the SQL script in `aws-fcj-container-app/database` to insert the data. To do this, first navigate to the `aws-fcj-container-app/database` directory to get the script path:

```bash
cd aws-fcj-container-app/database
echo $PWD/init.sql
```

![5.3.1.png](/images/5-configure-ec2/5.3.1.png)

Copy the path as we will use it later.

#### Connect to RDS

Now, we'll use the MySQL client installed earlier to connect to the RDS instance. First, go to the RDS Console:

- Select the RDS instance you created earlier.
- Copy the endpoint.

![5.3.2.png](/images/5-configure-ec2/5.3.2.png)

Use the following command to connect:

```bash
mysql -h "rds-endpoint" -u admin -p
```

![5.3.3.png](/images/5-configure-ec2/5.3.3.png)

Next, we will use the `source` command to run the SQL script. Paste the script path copied earlier and execute the command.

![5.3.4.png](/images/5-configure-ec2/5.3.4.png)

#### Verify Results

Check the database:

![5.3.5.png](/images/5-configure-ec2/5.3.5.png)

Check the data:

![5.3.6.png](/images/5-configure-ec2/5.3.6.png)
