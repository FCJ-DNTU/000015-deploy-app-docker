+++
title = "Sử dụng Docker Hub"
date = 2024
weight = 2
chapter = false
pre = "<b>8.2. </b>"
+++

#### Tạo repository trên Docker Hub

- Vào **Docker Hub** đã được chuẩn bị sẵn và tạo một repository trong đó
- Chọn **Create repository**

![RDS](/images/8-push-image/8.2.1.png)

- Chọn **Namespace** của mình
- Nhập tên repository: **`fcj-lab-docker`**
- Nhập mô tả: **`Store images`**
- Chọn public
- Kiểm tra lại và chọn **Create**

![RDS](/images/8-push-image/8.2.2.png)

- Hoàn tất tạo một **repository** trên **Docker Hub**

![RDS](/images/8-push-image/8.2.3.png)

#### Vào lại EC2 instance đã được ssh sẵn

- Vào lại **EC2**
- Đăng nhập vào **Docker**
```
sudo docker login
```

![RDS](/images/8-push-image/8.2.4.png)

- Gắn tag cho các images
```
sudo docker images
sudo docker tag <Image>:<Tag> <Account_name>/<Repository_name>:<Tag_Name>
sudo docker images
```

![RDS](/images/8-push-image/8.2.5.png)

- Gắn push images lên **Docker hub**
```
sudo docker images
sudo docker push <Account_name>/<Repository_name>:<Tag_Name>
```

![RDS](/images/8-push-image/8.2.6.png)

- Kiểm tra các image được push ở trong **Docker hub**

![RDS](/images/8-push-image/8.2.7.png)
