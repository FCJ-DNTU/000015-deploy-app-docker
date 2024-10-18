---
title: "Clean Up Resources"
date: 2024
weight: 9
chapter: false
pre: "<b>9. </b>"
---

### Clean Up Resources

{{% notice note %}}
**Note:** In the next section, we will explore Elastic Container Services and implement a CI/CD Pipeline, so we can skip some parts in the resource cleanup.
{{% /notice %}}

#### Clean Up Elastic Container Registry

On the AWS Console interface:

- Search for and select **Elastic Container Registry**.

![9.1](/images/9-clean-up/9.1.png)

You will see the two repositories we created earlier:

- Select **fcjresbar-be**.
- Click **Delete**.

![9.2](/images/9-clean-up/9.2.png)

- Confirm the **Delete** action.

![9.3](/images/9-clean-up/9.3.png)

Similarly, perform the same for the other repository:

- Select **fcjresbar-fe**.
- Click **Delete**.

![9.4](/images/9-clean-up/9.4.png)

- Confirm the **Delete** action.

![9.5](/images/9-clean-up/9.5.png)

#### Clean Up EC2

- Search for and select **EC2**.

![9.6](/images/9-clean-up/9.6.png)

- Select the EC2 instance we created, **FCJ-Lab-my-server**.

![9.7](/images/9-clean-up/9.7.png)

#### Delete Security Group

- Search for and select **VPC**.

![9.8](/images/9-clean-up/9.8.png)

In the left panel:

- Select **Security Groups**.
- Choose **FCJ-Lab-sg-private**.
- Click **Action**.
- Select **Delete security groups**.

![9.9](/images/9-clean-up/9.9.png)

Similarly:

- Select **Security Groups**.
- Choose **FCJ-Lab-sg-public**.
- Click **Action**.
- Select **Delete security groups**.

![9.10](/images/9-clean-up/9.10.png)

#### Delete Role

- Search for and select **IAM**.

![9.11](/images/9-clean-up/9.11.png)

In the left panel:

- Select **Roles**.
- Search for **customRWECRRole**.
- Select the created role.
- Click **Delete**.

![9.12](/images/9-clean-up/9.12.png)

- Enter `customRWECRRole`.
- Click **Delete**.

![9.13](/images/9-clean-up/9.13.png)

#### Clean Up VPC

- Search for and select **VPC**.
- Select **VPC-Lab-vpc**.
- Click **Action**.
- Select **Delete VPC**.

![9.14](/images/9-clean-up/9.14.png)

#### Clean Up RDS

On the AWS Console interface:

- Search for and select **RDS**.

![9.15](/images/9-clean-up/9.15.png)

- Select **Databases**.
- Choose the RDS instance we created.
- Click **Action**.
- Select **Delete**.

![9.16](/images/9-clean-up/9.16.png)

- Check **I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.**
- Enter `delete me`.
- Click **Delete**.

![9.17](/images/9-clean-up/9.17.png)
