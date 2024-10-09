+++
title = "Triển khai ứng dụng"
date = 2024
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

{{% notice note%}}
Để làm được phần này thì buộc bạn phải cài đặt được Git trước đó.
{{% /notice%}}

#### Tải mã nguồn

Tạo một folder với tên bất kỳ (mình đặt là `workspace`), click chuột phải chọn **Open in Terminal**.

**INSERT IMAGE HERE**

Clone mã nguồn của ứng dụng từ trên Github về trên máy.

**INSERT IMAGE HERE**

```bash
git clone https://github.com/FCJ-DNTU/fcj-resbar.git
```

**INSERT IMAGE HERE**

#### Thêm dữ liệu

Để thêm được dữ liệu:

- Vào trong thư mục `database` của thư mục chứa mã nguồn với tải về.
- Sao chép đường dẫn ở trên thanh Browse của window.
- Dán đường dẫn vào trong MySQL Shell, thêm tên của script (`init.sql`) vào trong chuỗi mới dán vào.

**INSERT IMAGE HERE**

Vào MySQL Shell để kết nối tới MySQL Server, các bước kết nối tương tự như ở phần trước. Trong thư mục của dự án, bạn sẽ để ý thấy có một thư mục tên là `database`, trong này chứa script SQL để tạo cơ sở dữ liệu, bảng, các ràng buộc và thêm dữ liệu. Trong bước này thì chúng ta sẽ dùng lệnh `source` để chạy script.

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Thực hiện một số truy vấn để kiểm tra

```sql
SELECT * FROM Clients;
```

**INSERT IMAGE HERE**

#### Triển khai Web Server

Sau khi dữ liệu đã được thêm thành công, thì giờ chúng ta sẽ khởi động Web Server, đầu tiên là vào trong thư mục `backend` sửa đổi lại nội dung trong file `.env`.

```bash
NODE_ENV=development
PORT=5000
JWT_SECRET=0bac010eca699c25c8f62ba86e319c2305beb94641b859c32518cb854addb5f4
# Thay Username của user đã thiết lập từ trước.
DB_USER=admin
DB_NAME=fcjresbar
# Thay Password của user đã thiết lập từ trước.
DB_PASSWORD=yourpassword
DB_HOST=localhost
DB_DIALECT=mysql
```

Mở **Terminal** ở trong thư mục này và tiến hành cài đặt các NPM Packages

```bash
npm install
```

**INSERT IMAGE HERE**

Sau đó là khởi chạy server

```bash
npm run dev
```

**INSERT IMAGE HERE**

Và Web Server đã chạy thành công.

#### Triển khai Client Application

Tiếp theo, mình sẽ triển khai ứng dụng người dùng cuối, vào trong thư mục `frontend`, mở **Terminal** và cài đặt các NPM Packages.

```bash
npm install
```

**INSERT IMAGE HERE**

Trước khi khởi chạy ứng dụng thì mình sẽ cần phải thay đổi lại nội dung trong file `vite.config.js` như đoạn cấu hình mẫu ở bên dưới

```js
/// <reference types="vite/client" />

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  server: {
    proxy: {
      "/api": {
        // API Endpoint của Web Server
        target: "http://localhost:5000/api",
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ""),
      },
    },
  },
});
```

{{% notice note%}}
Đoạn cấu hình trên là chúng ta đã cài đặt proxy cho Vite, nghĩa là khi có request url mà có /api ở trong đó, thì sẽ được thay thế bởi chuỗi **target**.
{{% /notice%}}

Khởi chạy ứng dụng

```bash
npm run dev
```

**INSERT IMAGE HERE**

#### Kết luận

Từ các bước triển khai từ đầu phần **Triển khai trên Local** này tới phần này, thì chúng ta có thể rút ra được một số điều sau:

- Triển khai thủ công rất cực, phải cài đặt rất nhiều thứ. Vì thế mà phần sau chúng ta sẽ dùng Linux và Docker để triển khai toàn bộ ứng dụng này.
- Nếu như ứng dụng được phát triển và triển khai trên nền tảng là Windows, thì khi chuyển sang các nền tảng khác thì cũng sẽ khó cho việc chuyển đổi.
- Nếu như chúng ta trển khai ứng dụng này lên môi trường thật, với chiến lược và kiến trúc như thế này thì hệ thống sẽ không mang tính đảm bảo cao.
- Không đảm bảo được "môi trường" cho các ứng dụng. Khi mà chúng ta triển khai như thế này, thì các ứng dụng đang xài chung một nguồn tài nguyên với nhau, và với các phần mềm khác ở trong máy. Đôi khi sẽ xảy ra một số lỗi từ một phần mềm hoặc ứng dụng khác, việc này sẽ làm ảnh hưởng tới hệ thống ứng dụng của chúng ta.
