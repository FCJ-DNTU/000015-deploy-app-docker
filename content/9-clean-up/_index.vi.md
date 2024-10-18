---
title: "Dọn Dẹp Tài Nguyên"
date: 2024
weight: 9
chapter: false
pre: "<b>9. </b>"
---

### Dọn Dẹp Tài Nguyên

{{% notice note %}}
**Lưu ý:** Trong phần tiếp theo, chúng ta sẽ tìm hiểu về Elastic Container Services và triển khai CICD Pipeline, vì vậy trong bước dọn dẹp tài nguyên, chúng ta có thể bỏ qua.
{{% /notice %}}

#### Dọn Dẹp Elastic Container Registry

Trên giao diện AWS Console:

- Tìm kiếm và chọn **Elastic Container Registry**.

![9.1](/images/9-clean-up/9.1.png)

Bạn sẽ thấy hai kho lưu trữ mà chúng ta đã tạo trước đó:

- Chọn **fcjresbar-be**.
- Nhấn **Delete**.

![9.2](/images/9-clean-up/9.2.png)

- Xác nhận hành động **Delete**.

![9.3](/images/9-clean-up/9.3.png)

Tương tự, thực hiện cho kho còn lại:

- Chọn **fcjresbar-fe**.
- Nhấn **Delete**.

![9.4](/images/9-clean-up/9.4.png)

- Xác nhận hành động **Delete**.

![9.5](/images/9-clean-up/9.5.png)

#### Dọn Dẹp EC2

- Tìm kiếm và chọn **EC2**.

![9.6](/images/9-clean-up/9.6.png)

- Chọn EC2 mà chúng ta đã tạo, **FCJ-Lab-my-server**.

![9.7](/images/9-clean-up/9.7.png)

#### Xoá Security Group

- Tìm kiếm và chọn **VPC**.

![9.8](/images/9-clean-up/9.8.png)

Tại bảng bên trái:

- Chọn **Security Groups**.
- Chọn **FCJ-Lab-sg-private**.
- Nhấn **Action**.
- Chọn **Delete security groups**.

![9.9](/images/9-clean-up/9.9.png)

Tương tự như trên:

- Chọn **Security Groups**.
- Chọn **FCJ-Lab-sg-public**.
- Nhấn **Action**.
- Chọn **Delete security groups**.

![9.10](/images/9-clean-up/9.10.png)

#### Xoá Role

- Tìm và chọn **IAM**.

![9.11](/images/9-clean-up/9.11.png)

Tại bảng bên trái:

- Chọn **Role**.
- Tìm kiếm **customRWECRRole**.
- Chọn role đã tạo.
- Nhấn **Delete**.

![9.12](/images/9-clean-up/9.12.png)

- Nhập `customRWECRRole`.
- Nhấn **Delete**.

![9.13](/images/9-clean-up/9.13.png)

#### Dọn Dẹp VPC

- Tìm kiếm và chọn **VPC**.
- Chọn **VPC-Lab-vpc**.
- Nhấn **Action**.
- Chọn **Delete VPC**.

![9.14](/images/9-clean-up/9.14.png)
