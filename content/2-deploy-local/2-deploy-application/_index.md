+++
title = "Deploy Application"
date = 2024
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

{{% notice note%}}
To complete this part, you must have Git installed beforehand.
{{% /notice%}}

#### Download Source Code

First,

- Create a folder with any name (I'll call it `workspace`).
- Right-click and select **Open in Terminal**.

![2.2.1](/images/2-deploy-local/2.2.1.png)

Clone the application's source code from GitHub to your machine.

**INSERT IMAGE HERE**

REPLACE HERE

And here is the result:

![2.2.2](/images/2-deploy-local/2.2.2.png)

#### Add Data

To add data:

- Go to the `database` folder inside the source code folder you downloaded.
- Copy the path from the Browse bar in Windows.
- Paste the path into MySQL Shell, adding the script name (`init.sql`) to the pasted string.

![2.2.3](/images/2-deploy-local/2.2.3.png)

Use MySQL Shell to connect to MySQL Server. The connection steps are similar to the previous section. In the project folder, you'll notice a `database` folder containing SQL scripts to create the database, tables, constraints, and add data. In this step, we'll use the `source` command to run the script.

![2.2.4](/images/2-deploy-local/2.2.4.png)

![2.2.5](/images/2-deploy-local/2.2.5.png)

Run some queries to verify:

REPLACE HERE

![2.2.6](/images/2-deploy-local/2.2.6.png)

#### Deploy Web Server

After the data is successfully added, we will start the Web Server. First,

- Go into the `backend` folder and modify the contents of the `.env` file.

REPLACE HERE

- Then open the **Terminal** in this folder.
- Proceed to install the NPM packages to run the server.

REPLACE HERE

![2.2.7](/images/2-deploy-local/2.2.7.png)

Next, start the server:

REPLACE HERE

![2.2.8](/images/2-deploy-local/2.2.8.png)

And the Web Server has successfully started.

#### Deploy Client Application

Next, I'll deploy the client application:

- Go to the `frontend` folder.
- Open the **Terminal** and install the NPM packages.

REPLACE HERE

![2.2.9](/images/2-deploy-local/2.2.9.png)

Before running the application, I need to update the content in the `vite.config.js` file, as shown in the sample configuration below:

REPLACE HERE

{{% notice note%}}
The above configuration sets up a proxy for Vite, meaning that when a request URL contains `/api`, it will be replaced by the **target** string.
{{% /notice%}}

Run the application:

```bash
npm run dev
```

![2.2.10](/images/2-deploy-local/2.2.10.png)

After this section, we'll check the deployment results.

#### Conclusion

From the deployment steps from the beginning of the Local Deployment section to this point, we can draw some conclusions:

- Manual deployment is exhausting, requiring a lot of installations. In the next section, we will use Linux and Docker to deploy the entire application.
- If the application is developed and deployed on Windows, switching to other platforms may be difficult.
- If we deploy this application to a real environment with this strategy and architecture, the system won't be highly reliable.
- It doesn't ensure the "environment" for the applications. When deploying this way, the applications share the same resources, and with other software on the machine. Sometimes errors from other software or applications may affect our system.
