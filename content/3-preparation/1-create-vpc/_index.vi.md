+++
title = "Cấu hình VPC"
date = 2024
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

### Cấu hình VPC

Ở giao diện AWS console thực hiện

- Tìm kiếm và chọn VPC

![3.1.1](/images/3-preparation/3.1.1.png)

Ở giao diện quản lý **VPC**

- Chọn **Your VPC**
- Chọn **Create VPC**

![3.1.2](/images/3-preparation/3.1.2.png)

Xuất hiện bảng cấu hình cho VPC

- Chọn **VPC and more**
- Đặt tên `FCJ-Lab`

![3.1.3](/images/3-preparation/3.1.3.png)

Ở phần VPC endpoint

- Chọn **None**
- Chọn **Create VPC**

![3.1.4](/images/3-preparation/3.1.4.png)

Sau khi tạo xong VPC, chúng ta tiến hành kiểm tra thông tin VPC vừa tạo.

- Chọn **FCJ-Lab-vpc**

![3.1.5](/images/3-preparation/3.1.5.png)

Xem tổng quan cấu hình của VPC

![3.1.6](/images/3-preparation/3.1.6.png)

### Cấu hình Public Subnet

Ở giao diện quản lý VPC, ở mục chọn ở bên trái kéo xuống dưới

- Chọn **Subnet**
- Tìm kiếm **FCJ-Lab**

![3.1.7](/images/3-preparation/3.1.7.png)

Chúng ta sẽ thấy có 2 FCJ-Lab-subnet-public-1a, FCJ-Lab-subnet-public-1b

Đầu tiên chúng ta sẽ setting cho FCJ-Lab-subnet-public-1a

- Chọn **FCJ-lab-subnet-public-1a**
- Chọn **Action**
- Chọn **Edit subnet settings**

![3.1.8](/images/3-preparation/3.1.8.png)

Xuất hiện bảng cấu hình cho public subnet

- Click chọn **Enable auto-assign public IPv4 address**
- Chọn **Save**

![3.1.9](/images/3-preparation/3.1.9.png)

Tương tự, chúng ta sẽ setting cho FCJ-Lab-subnet-public-1b

- Chọn **FCJ-Lab-subnet-public-1b**
- Chọn **Action**
- Chọn **Edit subnet settings**

![3.1.10](/images/3-preparation/3.1.10.png)

- Click chọn **Enable auto-assign public IPv4 address**
- Chọn **Save**

![3.1.11](/images/3-preparation/3.1.11.png)

Như vậy, chúng ta vừa cấu hình xong VPC và enable public IPv4 cho subnet public.
