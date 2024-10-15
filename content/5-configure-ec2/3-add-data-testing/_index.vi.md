+++
title = "Thêm cơ sở dữ liệu để thử nghiệm"
date = 2024
weight = 3
chapter = false
pre = "<b>5.3. </b>"
+++

#### Chuẩn bị

Để ứng dụng có thể hoạt động được, thì chúng ta cần phải thêm được dữ liệu vào trong RDS.

Chúng ta sẽ cần phải dùng sql script trong `aws-fcj-container-app/database` để có thể thêm được dữ liệu. Để có thể thêm được dữ liệu thì `cd` vào trong `aws-fcj-container-app/database` để lấy đường dẫn của script

```bash
cd aws-fcj-container-app/database
echo $PWD/init.sql
```

![5.3.1.png](/images/5-configure-ec2/5.3.1.png)

Copy lại đường dẫn đó, chúng ta sẽ dùng nó sau.

#### Kết nối tới RDS

Giờ thì chúng ta sẽ dùng mysql-client đã tải trước đó để kết nối vào trong RDS Instance. Trước tiên, vào trong RDS Console

- Chọn RDS Instance mà chúng ta đã tạo hồi nãy.
- Copy Endpoint.

![5.3.2.png](/images/5-configure-ec2/5.3.2.png)

```bash
mysql -h "rds-endpoint" -u admin -p
```

![5.3.3.png](/images/5-configure-ec2/5.3.3.png)

Sau đó chúng ta sẽ dùng lệnh `source` để chạy script sql, dán lại đường dẫn mà chúng ta mới sao chép ở bước trước và chạy lệnh.

![5.3.4.png](/images/5-configure-ec2/5.3.4.png)

#### Kiểm tra kết quả

Kiểm tra database

![5.3.5.png](/images/5-configure-ec2/5.3.5.png)

Kiểm tra dữ liệu

![5.3.6.png](/images/5-configure-ec2/5.3.6.png)
