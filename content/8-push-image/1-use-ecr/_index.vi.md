+++
title = "Sử dụng ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Tạo ECR repository

- Tìm kiếm **Amazon Elastic Container Registry**
- Chọn **Create**

![RDS](/images/8-push-image/8.1.1.png)

- Nhập tên: **`fcj-lab-ecr`**
- Chọn cấu hình cho phù hợp

![RDS](/images/8-push-image/8.1.2.png)

- Phần mã hóa để mặc định hoặc chọn cấu hình cho phù hợp
- Chọn để bật **Scan on push**
- Chọn **Create**

![RDS](/images/8-push-image/8.1.3.png)

- Hoàn tất tạo một repository trong ECR

![RDS](/images/8-push-image/8.1.4.png)

- Truy cập vào tên repository đó, chọn **View push commands** để xem cách push images

![RDS](/images/8-push-image/8.1.5.png)

#### Vào lại EC2 instance đã được ssh sẵn

- Tải **AWS CLI** bằng các lệnh sau
```
sudo apt -y update
sudo apt -y install unzip curl
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

![RDS](/images/8-push-image/8.1.6.png)

![RDS](/images/8-push-image/8.1.7.png)

- Giải nén và kiểm tra
```
sudo unzip awscliv2.zip
sudo ./aws/install
aws --version
```

![RDS](/images/8-push-image/8.1.8.png)

![RDS](/images/8-push-image/8.1.9.png)

- Đăng nhập vào **ECR** bằng lệnh mẫu sau
```
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
```
{{% notice note%}}
Nếu như bị lỗi phần này thì mình khuyến nghị bạn nên kiểm tra lại xem EC2 instance của bạn đã được cấp quyền truy cập ECR chưa nếu chưa cần phải cấp cho nó hoặc là dùng **aws config** để đăng nhập bằng credentials của AWS.
{{% /notice%}}

![RDS](/images/8-push-image/8.1.10.png)

- Build các image nginx đầu tiên 
```
ls
cd nginx/
sudo docker build -t fcj-nginx .
```

![RDS](/images/8-push-image/8.1.11.png)

- Build các image frontend 
```
cd ...
cd frontend/
sudo docker build -t fcj-frontend .
```

![RDS](/images/8-push-image/8.1.12.png)

- Build các image backend 
```
cd ...
cd backend/
sudo docker build -t fcj-backend .
```

![RDS](/images/8-push-image/8.1.13.png)

- Kiểm tra các images được build thành công
- Gắn tag cho từng images để có thể push lên ECR 
```
sudo docker images
sudo docker tag <image>:<tag> <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/<Repository_Name>:<Name_tag>
sudo docker images
```

![RDS](/images/8-push-image/8.1.14.png)

- Push images lên **ECR repository**
```
sudo docker images
sudo docker push <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/<Repository_Name>:<Name_tag>
sudo docker images
```
{{% notice note%}}
Nếu như bị lỗi phần này thì mình khuyên bạn nên chuyển qua sử dụng **root** để có thể tối ưu hóa quyền để push images lên ECR
{{% /notice%}}

![RDS](/images/8-push-image/8.1.15.png)

- Kiểm tra images được push ở trên **ECR repository**

![RDS](/images/8-push-image/8.1.16.png)