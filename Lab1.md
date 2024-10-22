### 1. Phân tích kiến trúc
#### Đề xuất kiến trúc 3 lớp 
1. Lớp giao diện 
2. Lớp nghiệp vụ
3. Lớp dữ liệu 

> Giải thích:
Kiến trúc 3 lớp phù hợp với hệ thống Payroll vì:
Tách biệt rõ ràng giữa giao diện, xử lý nghiệp vụ và truy xuất dữ liệu
Dễ dàng bảo trì, nâng cấp từng lớp độc lập
Có thể tái sử dụng lớp nghiệp vụ và dữ liệu cho các ứng dụng khác

#### Ý nghĩa các lớp:
- Lớp giao diện: Xử lý tương tác với người dùng
- Lớp nghiệp vụ: Chứa logic xử lý nghiệp vụ chính
- Lớp dữ liệu: Truy xuất và lưu trữ dữ liệu

#### Sơ đồ pakage
vẽ sau
### 2. Cơ chế phân tích
#### Các cơ chế cần giải quyết:

1. Xác thực và phân quyền người dùng
2. Lưu trữ và truy xuất dữ liệu (CSDL)
3. Tính toán lương và thuế
4. In ấn báo cáo
5. Giao tiếp với hệ thống ngân hàng
   
#### Giải thích:
- Xác thực và phân quyền: Đảm bảo an toàn thông tin
- Lưu trữ dữ liệu: Quản lý thông tin nhân viên, chấm công, lương
- Tính toán: Xử lý nghiệp vụ chính của hệ thống lương
- In ấn: Tạo báo cáo, phiếu lương
- Giao tiếp ngân hàng: Chuyển lương tự động
