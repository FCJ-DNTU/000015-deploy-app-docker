+++
title = "Triển khai Application"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Triển khai với Docker Compose

Trước khi triển khai với Docker Compose, thì chúng ta dừng lại 2 Docker Containers (Ctrl + C) vừa rồi đã chạy.

![7.1.1.png](/images/7-docker-compose/7.1.1.png)

![7.1.2.png](/images/7-docker-compose/7.1.2.png)

Tạo một SSH Session mới, sau đó vào trong thư mục `docker-compose-env` nằm ở gốc của dự án và sửa lại biến `DB_HOST`

![7.1.3.png](/images/7-docker-compose/7.1.3.png)

![7.1.4.png](/images/7-docker-compose/7.1.4.png)

Sau đó thì chúng ta chỉ đơn giản dùng

```bash
sudo docker compose -f docker-compose.app.yml up
```

Để khởi động 2 containers giống như ở phần trước mà chúng ta đã làm.

![7.1.5.png](/images/7-docker-compose/7.1.5.png)

![7.1.6.png](/images/7-docker-compose/7.1.6.png)

Ok vậy là ứng dụng của chúng ta có vẻ như đã hoạt động được, ở bước sau thì tiến hành kiểm tra ứng dụng.
