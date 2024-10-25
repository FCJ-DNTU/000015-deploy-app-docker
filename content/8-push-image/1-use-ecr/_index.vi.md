+++
title = "Sử dụng ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Tạo ECR Repository cho Frontend Image

- Tìm kiếm **Amazon Elastic Container Registry**
- Chọn **Create**

![8.1.1.png](/images/8-push-image/8.1.1.png)

Chúng ta sẽ tạo 2 repositories khác nhau để chứa các Docker Image. Đầu tiên là tạo repository để lưu image cho frontend app.

- Repository name: `fcjresbar-fe`.
- Image tag mutability: chọn **Mutable**.
- Encryption configuration: để mặc định.

![8.1.2.png](/images/8-push-image/8.1.2.png)

- Ấn **Create** để tạo

![8.1.3.png](/images/8-push-image/8.1.3.png)

![8.1.4.png](/images/8-push-image/8.1.4.png)

#### Tạo ECR Repository cho Backend Image

Tương tự, giờ thì chúng ta sẽ tạo cho Backend Image

![8.1.5.png](/images/8-push-image/8.1.5.png)

Với các thông tin:

- Repository name: `fcjresbar-be`.
- Image tag mutability: chọn **Mutable**.
- Encryption configuration: để mặc định.

![8.1.6.png](/images/8-push-image/8.1.6.png)

- Ấn **Create** để tạo

![8.1.7.png](/images/8-push-image/8.1.7.png)

![8.1.8.png](/images/8-push-image/8.1.8.png)

{{% notice note %}}
Chúng ta cần phải tạo mỗi một repository cho mỗi một ứng dụng khác nhau để quản lý version của các Docker image dễ dàng hơn, đặc biệt là dùng để thực hiện CI/CD sau này.
{{% /notice %}}

#### Cài AWS CLI

Theo mặc định (15/10/2024) thì AWS CLI không được cài đặt mặc định ở trong Ubuntu.

![8.1.9.png](/images/8-push-image/8.1.9.png)

Trước tiên thì chúng ta cần phải tải **unzip** trước.

```bash
sudo apt install unzip
```

![8.1.10.png](/images/8-push-image/8.1.10.png)

Sau đó thì chúng ta sẽ dùng các câu lệnh ở bên dưới để có thể cài đặt được AWS CLI.

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![8.1.11.png](/images/8-push-image/8.1.11.png)

![8.1.12.png](/images/8-push-image/8.1.12.png)

#### Push Frontend Image lên ECR

Vào lại ECR Console

- Chọn `fcjresbar-fe`
- Ấn **View push commands**

![8.1.13.png](/images/8-push-image/8.1.13.png)

Khi đó một hộp thoại sẽ nhảy lên và chúng ta có thể thấy được một chuỗi các câu lệnh.

![8.1.14.png](/images/8-push-image/8.1.14.png)

Trở lại với EC2 Instance, chúng ta cần phải dùng Root User để có thể đăng nhập vào trong ECR với Docker.

Ở AWS console của Push commands for fcjresbar-fe

- Chọn câu lệnh thứ nhất để xác thực đăng nhập vào Amazon Elastic Container Registry (ECR) từ môi trường Docker local của bạn. Trước đó hay đảm bảo rằng bạn đã cấu hình **AWS Configure**

![8.1.15.png](/images/8-push-image/8.1.15.png)

{{% notice note %}}
Bởi vì khi mà người dùng sử dụng sudo để đăng nhập vào ECR với Docker, thì credential được lưu ở trong HOME Dir của người dùng đó. Nhưng khi thực hiện lệnh push hoặc pull, thì nó sẽ xem credential ở trong Root thay vì là ở trong HOME Dir đã được lưu khi đăng nhập trước đó.
{{% /notice %}}

Ở các phần trước đó thì chúng ta đã tạo ra các Images cho từng ứng dụng rồi, nên là giờ chỉ cần gắn tag lại cho phù hợp rồi đẩy lên trên các Registry tương ứng.

```bash
docker image ls
```

Ở AWS console của Push commands for fcjresbar-fe

- Chọn dòng lệnh thứ 3 để thực hiện gắn tag, thay thế các tên resource image mà bạn tạo trước đó

{{% notice note %}}
Format chung `<Account_ID>.dkr.ecr.<region>.amazonaws.com/<Repository_Name>:<Name_tag>`
{{% /notice %}}

![8.1.16.png](/images/8-push-image/8.1.16.png)

Sau khi tạo xong thì tiến hành đẩy Image lên ECR

Ở AWS console của Push commands for fcjresbar-fe

- Chọn lệnh push

![8.1.17.png](/images/8-push-image/8.1.17.png)

#### Push Backend Image lên ECR

Tương tự, chúng ta cũng sẽ view push command của `fcjresbar-be`, nhớ sao chép lại lệnh đăng nhập. Nhưng logout ra trước

![8.1.18.png](/images/8-push-image/8.1.18.png)

Đăng nhập lại bằng lệnh đăng nhập đã sao chép

![8.1.19.png](/images/8-push-image/8.1.19.png)

Tương tự, gắn tag phù hợp cho image

![8.1.20.png](/images/8-push-image/8.1.20.png)

Đẩy image lên ECR

![8.1.21.png](/images/8-push-image/8.1.21.png)

#### Kiểm tra kết quả

Nếu như thành công, thì vào trong ECR Console, vào lần lượt từng repositories thì chúng ta có thể thấy được kết quả ở trong này.

![8.1.22.png](/images/8-push-image/8.1.22.png)

![8.1.23.png](/images/8-push-image/8.1.23.png)
