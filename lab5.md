# Thiết kế chức năng TimeCard và RunPayroll

## 1. TimeCard Management System

### Bước 1: Phân phối hành vi
- Ghi nhận thời gian làm việc của nhân viên.
- Cập nhật thời gian làm việc cho từng nhân viên.
- Lấy thông tin thời gian làm việc từ cơ sở dữ liệu.
- Xóa thông tin thời gian làm việc không còn cần thiết.

### Bước 2: Tài liệu hóa các phần tử
- **Các lớp**: 
  - `TimeCard`
- **Các thuộc tính**:
  - `employeeId`: ID của nhân viên.
  - `weekEnding`: Ngày kết thúc tuần.
  - `hoursWorked`: Số giờ làm việc.
- **Các phương thức**: 
  - `saveTimeCard(employeeId, weekEnding, hoursWorked)`
  - `updateTimeCard(employeeId, weekEnding, hoursWorked)`
  - `getTimeCard(employeeId, weekEnding)`
  - `deleteTimeCard(employeeId, weekEnding)`

### Bước 3: Mô tả các phụ thuộc
- Phụ thuộc vào Hệ thống con Quản lý Nhân viên để xác thực thông tin nhân viên.
- Phụ thuộc vào cơ sở dữ liệu để lưu trữ và truy xuất thông tin thời gian làm việc.

### Bước 4: Kiểm tra (Checkpoints)
- Đảm bảo các phương thức ghi nhận, cập nhật và xóa thông tin thời gian làm việc hoạt động chính xác.
- Kiểm tra khả năng lấy thông tin thời gian làm việc từ cơ sở dữ liệu.
- Đảm bảo thông tin thời gian làm việc không bị trùng lặp cho cùng một nhân viên trong cùng một tuần.

---

## 2. RunPayroll Management System

### Bước 1: Phân phối hành vi
- Tính toán lương cho tất cả nhân viên dựa trên thông tin thời gian làm việc và loại nhân viên.
- Lưu trữ thông tin lương vào cơ sở dữ liệu.
- Cung cấp báo cáo lương cho quản lý.
- Gửi thông báo đến nhân viên về lương đã được tính toán.

### Bước 2: Tài liệu hóa các phần tử
- **Các lớp**: 
  - `Payroll`
- **Các thuộc tính**:
  - `payrollDate`: Ngày tính lương.
  - `payrollRecords`: Danh sách các bản ghi lương.
- **Các phương thức**: 
  - `runPayroll(payrollDate)`
  - `calculateEmployeePay(employeeId)`
  - `savePayrollRecord(employeeId, paycheck)`
  - `generatePayrollReport()`

### Bước 3: Mô tả các phụ thuộc
- Phụ thuộc vào Hệ thống con Quản lý Thời gian làm việc để lấy thông tin thời gian làm việc của nhân viên.
- Phụ thuộc vào Hệ thống con Quản lý Nhân viên để xác định loại nhân viên và cách tính lương.
- Phụ thuộc vào cơ sở dữ liệu để lưu trữ thông tin lương và truy xuất thông tin nhân viên.

### Bước 4: Kiểm tra (Checkpoints)
- Đảm bảo tính toán lương chính xác cho từng nhân viên.
- Kiểm tra khả năng lưu trữ thông tin lương vào cơ sở dữ liệu.
- Đảm bảo báo cáo lương được tạo ra chính xác và đầy đủ thông tin.
- Kiểm tra khả năng gửi thông báo đến nhân viên về lương đã được tính toán.
