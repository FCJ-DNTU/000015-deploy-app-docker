+++
title = "Kiểm tra ứng dụng"
date = 2024
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

#### Kiểm tra kết quả triển khai

Đầu tiên, thì chúng ta sẽ cần vào đường dẫn đã được mở ra ở trong lần chiển khai trước đó `http://localhost:5173`. Khi đó thì chúng ta sẽ nhận được giao diện như sau

![2.3.1](/images/2-deploy-local/2.3.1.png)

Dùng 1 trong hai tài khoản sau để đăng nhập:

- User: email `user@example.com`; password `123456`.
- Admin: email `admin@example.com`; password `123456`.

Sau khi đăng nhập xong thì các bạn có thể thấy được nội dung ở bên web như sau

![2.3.2](/images/2-deploy-local/2.3.2.png)

Chuyển sang một số trang khác để xem thêm kết quả

![2.3.3](/images/2-deploy-local/2.3.3.png)

![2.3.4](/images/2-deploy-local/2.3.4.png)

Ok, vậy thì chứng tỏ là hệ thống ở dưới local của chúng ta đã triển khai thành công. Sang phần tiếp theo, chúng ta sẽ chuẩn bị triển khai lên **AWS Cloud** và dùng **Docker**.
