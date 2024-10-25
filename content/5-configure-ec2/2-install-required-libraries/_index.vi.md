+++
title = "Cài đặt các thư viện yêu cầu"
date = 2024
weight = 3
chapter = false
pre = "<b>5.2. </b>"
+++

Đầu tiên thì chúng ta sẽ phải kết nối SSH vào trong EC2 Instance mà chúng ta vừa mới tạo. Và thực hiện một số câu lệnh để cập nhật thông tin, gói cài đặt ở trong máy.

```bash
sudo apt update -y
sudo apt upgrade -y
```

![5.2.1.png](/images/5-configure-ec2/5.2.1.png)

![5.2.2.png](/images/5-configure-ec2/5.2.2.png)

#### Cài đặt Docker

Chúng ta sẽ phải cài đặt Docker để triển khai các ứng dụng sau này. Chúng ta sẽ sử dụng các câu lệnh sau để cài đặt

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

![5.2.3.png](/images/5-configure-ec2/5.2.3.png)

Sau đó là tiến hành cài đặt các thư viện liên quan cho docker

```bash
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

![5.2.4.png](/images/5-configure-ec2/5.2.4.png)

#### Cài đặt MySQL Client

Để có thể thêm được dữ liệu vào trong RDS, thì cần phải có MySQL Client. Tiến hành cài đặt MySQL Client.

```bash
sudo apt install mysql-client
```

![5.2.5.png](/images/5-configure-ec2/5.2.5.png)

### Kiểm tra kết quả

Kiểm tra Docker

![5.2.6.png](/images/5-configure-ec2/5.2.6.png)

Kiểm tra MySQL Client

![5.2.7.png](/images/5-configure-ec2/5.2.7.png)

Và để có thể clone được mã nguồn thì cần phải có Git. Kiểm tra thử Git

![5.2.8.png](/images/5-configure-ec2/5.2.8.png)

Ok, vậy là mọi thứ đã được cài đặt ổn định.

### Clone mã nguồn từ Github

Trước khi đi tới phần tiếp theo, thì chúng ta sẽ cần phải clone mã nguồn của dự án trước.

```bash
git clone https://github.com/AWS-First-Cloud-Journey/aws-fcj-container-app.git
```

![5.2.9.png](/images/5-configure-ec2/5.2.9.png)
