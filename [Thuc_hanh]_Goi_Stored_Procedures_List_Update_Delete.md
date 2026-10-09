# [Thực hành] Gọi Stored Procedures từ JDBC (List / Update / Delete)

## Mục tiêu

Luyện tập sử dụng Stored Procedures với JDBC.

## Mô tả

Cập nhật ứng dụng WEB quản lý User.

Cụ thể như sau:

* Gọi Stored Procedures từ JDBC sử dụng `CallableStatement` cho chức năng **hiển thị danh sách users**
* Gọi Stored Procedures từ JDBC sử dụng `CallableStatement` cho chức năng **sửa thông tin user**
* Gọi Stored Procedures từ JDBC sử dụng `CallableStatement` cho chức năng **xoá user**

## Hướng dẫn

### Bước 1: Định nghĩa các Stored Procedures

Tạo các Stored Procedures trong cơ sở dữ liệu MySQL (database `demo`) cho các chức năng:

- Lấy danh sách tất cả users
- Cập nhật thông tin user
- Xoá user theo id

### Bước 2: Trên ứng dụng, cập nhật interface `IUserDAO`

Thêm khai báo của các phương thức mới sử dụng Stored Procedure.

### Bước 3: Cập nhật lớp `UserDAO`

Override các phương thức vừa khai báo, sử dụng `CallableStatement` với cú pháp `{CALL procedure_name(...)}`.

### Bước 4: Cập nhật lớp `UserServlet`

Thay đổi logic điều hướng để gọi các phương thức mới (danh sách, sửa, xoá) thay vì dùng câu lệnh SQL trực tiếp.

### Bước 5: Chạy lại ứng dụng và test các chức năng

1. Biên dịch dự án (`mvn clean package`).
2. Triển khai lại lên Tomcat (Restart / Redeploy).
3. Kiểm thử:
   - Hiển thị danh sách users
   - Sửa thông tin một user
   - Xoá một user
