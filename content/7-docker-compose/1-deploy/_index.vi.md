+++
title = "Triển khai Application"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Triển khai với Docker Compose

Chúng ta đã có dự án được git clone về từ những phần trước. Truy cập vào **aws-fcj-container-app/docker-compose-env**.

![Image](/images/7-docker-compose/1-deploy/7.1.png?featherlight=false&width=90pc)

Trong thư mục này chúng ta chỉnh sửa file **backend.app.env** để thay đổi môi trường cho backend.

![Image](/images/7-docker-compose/1-deploy/7.2.png?featherlight=false&width=90pc)

Tiến hành thay đổi biến **DB_HOST** phù hợp với **RDS** mà chúng ta đã tạo ra ở phần trước. Sau đó lưu lại file.

![Image](/images/7-docker-compose/1-deploy/7.3.png?featherlight=false&width=90pc)

Tại thư mục **aws-fcj-container-app** chúng ta thực hiện build các image cho backend, frontend, nginx.

![Image](/images/7-docker-compose/1-deploy/7.4.png?featherlight=false&width=90pc)

Thực hiện build thành công các image.

![Image](/images/7-docker-compose/1-deploy/7.5.png?featherlight=false&width=90pc)



