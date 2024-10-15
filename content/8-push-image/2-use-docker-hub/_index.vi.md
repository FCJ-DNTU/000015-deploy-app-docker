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

![8.2.1.png](/images/8-push-image/8.2.1.png)

- Chọn **Namespace** là account của mình
- Nhập tên repository: `fcjresbar-fe`
- Nhập mô tả: `Frontend Image of FCJ Resbar`
- Chọn public
- Kiểm tra lại và chọn **Create**

![8.2.2.png](/images/8-push-image/8.2.2.png)

- Hoàn tất tạo một **repository** trên **Docker Hub**

![8.2.3.png](/images/8-push-image/8.2.3.png)

Tương tự, chúng ta tạo repository cho backend image.

- Chọn **Namespace** là account của mình
- Nhập tên repository: `fcjresbar-be`
- Nhập mô tả: `Backend Image of FCJ Resbar`
- Chọn public
- Kiểm tra lại và chọn **Create**

![8.2.4.png](/images/8-push-image/8.2.4.png)

Kết quả

![8.2.5.png](/images/8-push-image/8.2.5.png)

#### Push frontend image lên Docker Hub

Giờ thì chúng ta đã sẵn sàng đẩy các image lên trên từng repositories.

Logout và đăng nhập vào Docker Hub. Nhờ là đăng nhập đúng tài khoản và mật khẩu của tài khoản mà bạn đã tạo các repositories ở bước vừa rồi.

![8.2.6.png](/images/8-push-image/8.2.6.png)

Thay đổi tag cho frontend image

![8.2.7.png](/images/8-push-image/8.2.7.png)

Đẩy frontend image lên Docker Hub

![8.2.8.png](/images/8-push-image/8.2.8.png)

#### Push backend image lên Docker Hub

Tương tự, giờ thì chúng ta đánh tag nhanh và push image lên Docker Hub

![8.2.9.png](/images/8-push-image/8.2.9.png)

#### Kết quả

Sau khi push xong, thì chúng ta có thể thấy được các image đã được đẩy lên trên từng repository.

![8.2.10.png](/images/8-push-image/8.2.10.png)

![8.2.11.png](/images/8-push-image/8.2.11.png)
