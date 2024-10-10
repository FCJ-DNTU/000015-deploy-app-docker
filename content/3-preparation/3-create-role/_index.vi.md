+++
title = "Tạo IAM Roles để truy cập vào ECR"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

#### Cấu hình Policy

Ở giao diện AWS Console

- Chọn tìm và chọn `IAM`

![3.3.1](/images/3-preparation/3.3.1.png)

Ở mục chọn ở bên phải

- Chọn **Policy**
- Chọn **Create Policy**

![3.3.2](/images/3-preparation/3.3.2.png)

Ở phần Policy Editor

- Tìm kiếm và chọn **Elastic Container Registry**
- Chọn **Next**

![3.3.3](/images/3-preparation/3.3.3.png)

Xuất hiện bảng chọn các rule

- Ở phần **List**
  - Chọn **DescribeImage**
  - ListImages
- Ở phần **Read**
  - Chọn **BatchGetImage**
  - Chọn **DescribeRegister**
  - Chọn **DescribeRepositories**
  - Chọn **GetAccountSetting**
  - Chọn **GetAuthorizationToken**

![3.3.4](/images/3-preparation/3.3.4.png)

- Ở phần **Resources**
  - Chọn **Specific**
  - Chọn **Any in this account**
  - Chọn **Next**

![3.3.5](/images/3-preparation/3.3.5.png)

- Ở phần Policy detail
  - Policy name `ReadECRRepositoryContent`
  - Description `Allow pull images, describe repositories`

![3.3.6](/images/3-preparation/3.3.6.png)

- Chọn **Create policy**

![3.3.7](/images/3-preparation/3.3.7.png)

Tương tự chúng ta tạo thêm một policy dành cho write ECR

- Chọn **Create Policy**

Xuất hiện bảng chọn các rule

- Ở phần **Read**
  - Chọn **BatchCheckLayerAvailability**
  - Chọn **GetAuthorizationToken**
- Ở phần **Write**
  - Chọn **Chọn CompleteLayerUpload**
  - Chọn **InitialLayerUpload**
  - Chọn **PutImage**
  - Chọn **UploadLayerPart**

![3.3.8](/images/3-preparation/3.3.8.png)

- Ở phần **Resources**
  - Chọn **Any in this account**
  - Chọn **Next**

![3.3.9](/images/3-preparation/3.3.9.png)

Xuất hiện bảng Policy detail

- Policy name **WriteECRRepositoryContent**
- Description **Allow push and delete images**

![3.3.10](/images/3-preparation/3.3.10.png)

- Chọn **Create policy**

![3.3.11](/images/3-preparation/3.3.11.png)

#### Tạo Role cho ECR

Ở giao diện quản lý EC2

- Chọn **Roles**
- Chọn **Create role**

![3.3.12](/images/3-preparation/3.3.12.png)

- Chọn **AWS service**
- Chọn **EC2**

![3.3.13](/images/3-preparation/3.3.13.png)

- Chọn **Next**

![3.3.14](/images/3-preparation/3.3.14.png)

- Filter by Type **Customer managed**
- Chọn 2 policy mà chúng ta vừa tạo
- Chọn **Next**

![3.3.15](/images/3-preparation/3.3.15.png)

- Role name **CustomRWECRRole**
- Description **Custom Read and Write role ECS**

![3.3.16](/images/3-preparation/3.3.16.png)

- Chọn **Create role**

![3.3.17](/images/3-preparation/3.3.17.png)
