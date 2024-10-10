+++
title = "Kiểm tra Application"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

#### Kết quả triển khai

Quay lại trong EC2 Console, chúng ta cần sẽ sao chép lại Public IPv4 của EC2 mà nãy giờ chúng ta đã thao tác, sau đó là thêm vào trình duyệt URL như sau

```
http://public-dns-of-your-ec2:3000
```

{{% notice note%}}
NginX hoạt động ở Port **80** trong container, khi mà chúng ta request tới URL trên, thì container sẽ đổi từ port **3000** -> **80**, NginX sẽ xử lý và chuyển tiếp yêu cầu của chúng ta tới FrontEnd Application và nội dung của Website sẽ được tải về.
{{% /notice%}}

![6.2.1](/images/6-docker-image/6.2.1.png)

Thử đăng nhập với User, nếu như đăng nhập thành công thì có nghĩa là ứng dụng của chúng ta đã hoạt động bình thường và chuyển chúng ta về giao diện chính.

![6.2.2](/images/6-docker-image/6.2.2.png)

![6.2.3](/images/6-docker-image/6.2.3.png)

Mở thêm một số trang khác

![6.2.4](/images/6-docker-image/6.2.4.png)

![6.2.5](/images/6-docker-image/6.2.5.png)

Như vậy thì chúng ta đã triển khai ứng dụng thành công với Docker Image. Sang phần sau thì chúng ta sẽ dùng một giải pháp khác để triển khai ứng dụng với Docker Compose, với giải pháp này thì việc triển khai, quản lý các containers sẽ dễ hơn.
