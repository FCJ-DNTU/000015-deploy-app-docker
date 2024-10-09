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
NginX hoạt động ở Port 3000, khi mà chúng ta request tới URL trên, thì NginX sẽ xử lý và chuyển tiếp yêu cầu của chúng ta tới FrontEnd Application. Khi đó thì nội dung của Web site sẽ được tải về.
{{% /notice%}}

**INSERT IMAGE HERE**

Thử đăng nhập với User, nếu như đăng nhập thành công thì có nghĩa là ứng dụng của chúng ta đã hoạt động bình thường và chuyển chúng ta về giao diện chính.

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Mở thêm một số trang khác

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Như vậy thì chúng ta đã triển khai ứng dụng thành công với Docker Image. Sang phần sau thì chúng ta sẽ dùng một giải pháp khác để triển khai ứng dụng với Docker Compose.
