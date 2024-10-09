+++
title = "Cài đặt Dependencies"
date = 2024
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note%}}
Trong bài này thì chúng ta sẽ thực hành trên máy Windows.
{{% /notice%}}

#### Cài đặt NodeJS

Để cho dễ hình dung hơn, thì bạn nên theo dõi video dưới đây để cài đặt NodeJS trên máy vi tính cá nhân của bạn.

{{< youtube 4FAtFwKVhn0 >}}

#### Cài đặt MySQL Community

Tương tự, xem thêm video này để cài đặt MySQL

{{< youtube u96rVINbAUI >}}

Một số lưu ý khi cài đặt MySQL:

- Các bạn nên cài cả **MySQL Client** và **MySQL Server** để tiện kiểm tra, đồng thời là cài luôn **MySQL Workbench** và **MySQL Shell**, là một hệ quản trị cơ sở dữ liệu giống với Microsoft SQL Server Management Studio của Microsoft SQL Server. Và có thể sau này bạn sẽ cần nó trong một số dự án khác.
- Trong MySQL cũng sẽ có 2 users là Root User và các User còn lại, các user này sẽ có các vai trò khác nhau. Nhưng phải luôn nhớ mật khẩu của Root User, đồng thời là thêm một tài khoản mới khi cài đặt MySQL Server.

#### Kết quả

Khi cài đặt NodeJS xong, chúng ta sẽ có được luôn npm ở trong gói cài đặt đó, kiểm tra xem NodeJS và NPM đã cài đặt thành công hay chưa thông qua 2 câu lệnh

```bash
node -v
npm -v
```

**INSERT IMAGE HERE**

#### Sử dụng MySQL Shell

Nhập `MySQL Shell` trên thanh tìm kiểm của windows, sau đó ấn chọn `MySQL Shell`.

**INSERT IMAGE HERE**

Khi mở lên thì chúng ta sẽ có được giao diện như sau

**INSERT IMAGE HERE**

Gõ `\sql` để chuyển Input Mode sang MySQL.

**INSERT IMAGE HERE**

Sau đó là chúng ta sẽ kết nối tới MySQL Server

**INSERT IMAGE HERE**

{{% notice note%}}
Nếu như bạn không tạo user trong quá trình cài đặt MySQL, thì có thể kết nối tới MySQL Server bằng Root User, khi đó **connection string** sẽ là `root@localhost` và nhớ nhập mật khẩu cho Root User mà bạn đã đặt trong quá trình cài đặt.
{{% /notice%}}

Dùng lệnh `SHOW DATABASES;` để kiểm tra kết quả lần nữa.

**INSERT IMAGE HERE**

Khi ra được kết quả này thì có nghĩa là bạn đã cài đặt đúng phần này và có thể chuyển tiếp tới phần tiếp theo.
