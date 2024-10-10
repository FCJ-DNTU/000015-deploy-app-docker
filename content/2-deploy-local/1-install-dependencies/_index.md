+++
title = "Install Dependencies"
date = 2024
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note%}}
In this article, we will practice on a Windows machine.
{{% /notice%}}

#### Install NodeJS

For better understanding, you should follow the video below to install NodeJS on your personal computer.

{{< youtube 4FAtFwKVhn0 >}}

#### Install MySQL Community

Similarly, watch this video to install MySQL:

{{< youtube u96rVINbAUI >}}

Some notes when installing MySQL:

- You should install both **MySQL Client** and **MySQL Server** for easier testing. Also, install **MySQL Workbench** and **MySQL Shell**, which is a database management system similar to Microsoft SQL Server Management Studio for Microsoft SQL Server. You may need them in some future projects.
- In MySQL, there are two types of users: Root User and other users, each with different roles. Always remember the password for the Root User, and add a new account when installing MySQL Server.

#### Results

Once NodeJS is installed, npm will also be included in the package. Check whether NodeJS and npm have been successfully installed using the following two commands:

```bash
node -v
npm -v
```

![2.1.1](/images/2-deploy-local/2.1.1.png)

#### Using MySQL Shell

Search for `MySQL Shell` in the Windows search bar, then select `MySQL Shell`.

![2.1.2](/images/2-deploy-local/2.1.2.png)

When opened, you will see the following interface:

![2.1.3](/images/2-deploy-local/2.1.3.png)

Type `\sql` to switch the Input Mode to MySQL.

![2.1.4](/images/2-deploy-local/2.1.4.png)

Then, connect to the MySQL Server.

![2.1.5](/images/2-deploy-local/2.1.5.png)

{{% notice note%}}
If you didn’t create a user during the MySQL installation, you can connect to the MySQL Server using the Root User. In that case, the **connection string** will be `root@localhost`, and don't forget to enter the Root User password you set during installation.
{{% /notice%}}

Use the `SHOW DATABASES;` command to check the result again.

![2.1.6](/images/2-deploy-local/2.1.6.png)

If you get this result, it means you have installed this part correctly and can proceed to the next section.
