+++
title = "Tạo DB Subnet Group"
date = 2024
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

#### Tạo Subnet Group DB

- Tìm kiếm từ khóa: **RDS** 
- Chọn phần: **Subnet groups**
- Chọn: **Create DB subnet group**

![RDS](/images/4-rds/4.1.1.png)

- Nhập tên: **`fcj-lab-subnet-group-db`**
- Nhập mô tả: **`Subnet Group for FCJ Management`**
- Chọn VPC đã được tạo từ trước là **FCJ-Lab-vpc**

![RDS](/images/4-rds/4.1.2.png)

- Chọn **Availability Zones** đã được tạo chung với **VPC** từ trước đó
- Chọn 2 **Subnet private**
- Kiểm tra lại và chọn **Create**

![RDS](/images/4-rds/4.1.3.png)

- Hoành thành tạo một **Subnet groups**

![RDS](/images/4-rds/4.1.4.png)
