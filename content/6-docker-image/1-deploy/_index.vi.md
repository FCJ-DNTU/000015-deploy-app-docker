+++
title = "Triển khai Application"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

Ở phần **2 Deploy on Local** trước đó thì chúng ta đã triển khai thủ công lần lượt là

- Database Server
- NginX Server
- Web Server
- End User Application

Có rất nhiều mặt hạn chế như mình đã nói trước đó, nên giờ chúng ta sẽ triển khai hạ tầng này ở trên Cloud với Docker, nên là việc tải về và cài đặt chúng ta sẽ không còn lo nữa. Nếu như bạn nắm được các khái niệm cơ bản của Docker (đặt biệt là mạng) thì phần này sẽ không quá khó.

Và ở bước **4 Configure RDS** trước đó thì chúng ta đã cấu hình Database Server với Amazon RDS, nên về mặt kỹ thuật, bảo trì và đảm bảo về truy cập cũng như an toàn dữ liệu thì mình sẽ không cần phải lo quá nhiều nữa. Nên là trong phần triển khai trên Cloud này thì mình chỉ quan tâm tới triển khai các ứng dụng còn lại với Docker Image.

Ở phần sau thì chúng ta sẽ triển khai với Docker Compose, để cho bạn có thể thấy được sự khác biệt khi deploy ở Local, với Docker Image trên Cloud và với Docker Compose trên Cloud.

#### Triển khai Web Server

Đầu tiên thì mình sẽ cần phải có Endpoint của RDS mà trước đó chúng ta đã tạo.

- Vào RDS Console.
- Chọn RDS Instance mà mình mới tạo.
- Sao chép lại Endpoint.

![6.1.1](/images/6-docker-image/6.1.1.png)

Thư mục mã nguồn

![6.1.2](/images/6-docker-image/6.1.2.png)

Vào trong thư mục mã nguồn mà chúng ta đã clone từ trước đó `aws-fcj-container-app`, trong thư mục `backend`, chúng ta sẽ sửa lại nội dung của `.env`, cụ thể là thay đổi biến `DB_HOST`

![6.1.3](/images/6-docker-image/6.1.3.png)

![6.1.4](/images/6-docker-image/6.1.4.png)

Giờ thì web server của chúng ta cũng đã sẵn sàng để chạy, tiếp theo là chạy lệnh ở bên dưới

```bash
docker build . -t backend-image
```

![6.1.5](/images/6-docker-image/6.1.5.png)

Trước khi bắt đầu chạy Container cho web server, thì mình sẽ cần phải tạo một **network** cho các container trong môi trường giao tiếp với nhau

```bash
docker network create my-network
```

Sau đó là tiến hành chạy Docker Container với Docker Image vừa mới tạo

```bash
docker run -p 5000:5000 --network my-network --name backend backend-image
```

![6.1.7](/images/6-docker-image/6.1.7.png)

#### Triển khai Application

Giờ chúng ta sẽ phải mở một SSH Session mới để thực hiện tương tự như các bước ở trên, nhưng sẽ là triển khai Application

![6.1.8](/images/6-docker-image/6.1.8.png)

- `cd` vào trong thư mục `frontend`
- Chạy lệnh như bên dưới

```bash
docker build . -t frontend-image
```

![6.1.9](/images/6-docker-image/6.1.9.png)

Sau đó là tiến hành chạy Docker Container với Docker Image vừa mới tạo

```bash
docker run --network my-network --name frontend frontend-image
```

![6.1.10](/images/6-docker-image/6.1.10.png)

#### Triển khai Nginx Server

Mở một Session khác, trước khi khởi tạo NginX Server, thì kiểm tra xem các container trước đó vẫn còn chạy hay không

```bash
docker ps
```

![6.1.11](/images/6-docker-image/6.1.11.png)

Ok, vậy là vẫn chạy như bình thường.

Và để cho hệ thống hoạt động trơn tru, thì chúng t sẽ thêm một bước nữa là triển khai thêm Nginx Server. Đóng vai trò là một Proxy Server. Tiến hành khởi động Nginx Server

- `cd` vào trong `nginx`
- Chạy lệnh như bên dưới

```bash
docker build . -t nginx-image
```

![6.1.12](/images/6-docker-image/6.1.12.png)

Sau đó là tiến hành chạy Docker Container với Docker Image vừa mới tạo

```bash
docker run -p 3000:80 --network my-network --name nginx nginx-image
```

![6.1.13](/images/6-docker-image/6.1.13.png)

Như vậy thì ứng dụng đã sẵn sàng để thử.
