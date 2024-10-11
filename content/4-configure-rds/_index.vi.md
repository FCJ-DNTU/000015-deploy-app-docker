+++
title = "Khởi chạy RDS Instance"
date = 2024
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Tổng quan RDS
Amazon RDS là cơ sở dữ liệu được quản lý trên AWS, chúng ta chỉ truy cập và quản lý ở mức RDBMS, không thể truy cập và quản lý ở mức hệ điều hành. Bao gồm Aurora, MySQL, PostgreSQL, MSSQL, Oracle, và MariaDB. Amazon RDS cung cấp các tính năng:

- Tự động sao lưu (cả log và database – tối đa 35 ngày).
- Tạo bản sao chỉ đọc (Read Replica) phục vụ cho các workload đọc (reporting).
- Read Replica có thể được tách ra và chuyển thành một Primary node.
- Chạy với cơ chế tự động failover, Primary/Standby, hay còn gọi là cơ chế Multi-AZ.
- RDS thường được sử dụng cho các ứng dụng OLTP.
- RDS cung cấp tính năng mã hóa dữ liệu at rest và in transit.
- RDS cũng được bảo vệ bởi tính năng tường lửa giống như EC2 (Security Group và NACL).
- Thay đổi quy mô (thay đổi instance size).
- Tự động tăng dung lượng lưu trữ (Storage Auto Scale).

#### Nội dung

1. [Tạo DB Subnet Group](1-create-db-subnet-group)
2. [Khởi chạy RDS Instance](2-launch-rds-instance)