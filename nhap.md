# Phân tích Ca sử dụng

## 1. Ca sử dụng: Create Administrative Report

### a. Các lớp phân tích
- **Lớp Boundary**: `PayrollAdministratorUI`
- **Lớp Controller**: `ReportController`
- **Lớp Entities**: `ReportGenerator`, `Report`, `ReportStorage`

### b. Biểu đồ tuần tự
![Sequence Create Administrative Report](https://www.planttext.com/api/plantuml/png/V591Zi8m3Bpd5JvI2Vg07X0h3eWBMYtY0TxMe4XfKXmNgM_Zi4_QBsneKrP5AQV4Oy-CxUJt_hFnWYnjRHIMuXW-iMDdp4TLQwkzC0PGVRlMLiXTCdlQgz9P2JXyKUDOjaDaY1LPqT95V4UM1hq9F8sE8OyNKYfb1QlrJ0i5C5rRyX9RO4BHpYwofCvf_r1wxRQ0ya6Z0L_aUPwfrvf_tdEQ0Yx3TIIEh6S5h99kSVnvYxYB0ZpUHd7kZoMSjQ43rhG4uyf-rj4sicPCmrETDTSz8s7zPi6Lzet1Rj97fZPag_1x_W000F__0m00)


### c. Nhiệm vụ của từng lớp phân tích
- **PayrollAdministratorUI**: Giao diện cho quản trị viên nhập tiêu chí báo cáo.
- **ReportController**: Điều phối việc tạo và lưu báo cáo.
- **ReportGenerator**: Tạo báo cáo dựa trên tiêu chí.
- **Report**: Chứa nội dung báo cáo.
- **ReportStorage**: Lưu báo cáo vào vị trí chỉ định.

### d. Một số thuộc tính và phương thức
- **PayrollAdministratorUI**:
  - `requestReportCreation()`
  - `displayReport(report: Report)`
  - `requestSaveReport()`
  - `displayErrorMessage()`

- **ReportController**:
  - `createReport(...)`
  - `saveReport(report: Report, fileName: String, location: String)`
  - `displayError(error: String)`

- **ReportGenerator**:
  - `generateReport()`
  - `validateCriteria()`

- **Report**:
  - `getContent()`
  - `setContent()`
  - `getSummary()`

- **ReportStorage**:
  - `saveReport()`
  - `validateLocation()`

### e. Mối quan hệ giữa các lớp
- `PayrollAdministratorUI` gửi yêu cầu tạo hoặc lưu báo cáo đến `ReportController`.
- `ReportController` gọi `ReportGenerator` để tạo báo cáo và `ReportStorage` để lưu báo cáo.
- `ReportGenerator` trả về đối tượng `Report` cho `ReportController`.
- `ReportStorage` lưu trữ báo cáo vào vị trí chỉ định.

### f. Biểu đồ lớp

![Class Create Administrative Report ](https://www.planttext.com/api/plantuml/png/V991QiCm44NtEeMM3YG-G1Ob9PHII4EewG46Use4ifJEo05JUh8kUgHUeR8jnRNLrWiRp_pvVd_ahu_F7JiWrpPQb1gOvGawibhVLeqoYXs1i_Jy8D-4x2_2rnRPFU7PajiJWbFMPAknMIa-Q-Z6PaR3Ool7rzLile0B1jbyzex8qYCoGus-zIu2LVYWDQw7GueyPOyGhV8y3suy-Synrl95QJn2WrjPE5AcNajjoo56hFn2b65_dmGBhdiqE2mgOjLZOP7n0bfLlhedvP0Kf06d-I4hckii9nMlATgc0UfIdyAp-0r6EqxM7L4E8VjeySVPRpOtoG68v4GcrNKT_ua2ebXkS5A8UPOVZHsQol-ntm000F__0m00)

#### Giải thích
- Actors: User
- Boundary Classes:
  - PayrollAdministratorUI: Giao diện để quản trị viên nhập tiêu chí báo cáo. Nó thu thập dữ liệu từ người dùng và gửi yêu cầu đến controller.
  - ReportDisplay: Hiển thị báo cáo sau khi được tạo.
- Control Classes:
  - ReportController: Điều phối quá trình tạo và lưu báo cáo. Nó nhận dữ liệu từ giao diện và gọi generator để tạo báo cáo.
- Entity Classes:
  - ReportGenerator: Thực hiện logic tạo báo cáo dựa trên tiêu chí đã nhập.
  - Report: Đại diện cho báo cáo được tạo.
  - ReportStorage: Chịu trách nhiệm lưu trữ báo cáo vào vị trí chỉ định.

---

## 2. Ca sử dụng: Create Employee Report

### a. Các lớp phân tích
- **Lớp Boundary**: `EmployeeReportUI`
- **Lớp Controller**: `EmployeeReportController`
- **Lớp Entities**: `EmployeeReportGenerator`, `EmployeeReport`, `EmployeeReportStorage`

### b. Biểu đồ tuần tự
![Sequence Create Employee Report](https://www.planttext.com/api/plantuml/png/Z99D2i8m48NtESKi5MeFq8K88kB6XU81ndQKG9hKwLJesLnu9AzWxP-O5dMLyEQzoPT97hVx8XTaALAZC1R7i4epuqeYTNI5JP3BNjbHvbWE6nKxA-oCLrWsgY5MP4MB7roJ9SRgYF7okBgl_7WcfJePPlC1K0HCbu9oQK6OKBIpawdodSFqcpg2-1LizKaOXdx-xHtswMyNmRdPTetyBhqJPbzflF7yZzBEB88Shnq4rqi09sreYoa5O5nSJyd7QzC_uAelSDASrXs-e8q-LgBpp63vGJPL2x99zGkV0000__y30000)

### c. Nhiệm vụ của từng lớp phân tích
- **EmployeeReportUI**: Giao diện cho nhân viên để nhập tiêu chí báo cáo.
- **EmployeeReportController**: Điều phối việc tạo và lưu báo cáo nhân viên.
- **EmployeeReportGenerator**: Tạo báo cáo nhân viên dựa trên tiêu chí.
- **EmployeeReport**: Chứa nội dung báo cáo nhân viên.
- **EmployeeReportStorage**: Lưu báo cáo nhân viên vào vị trí chỉ định.

### d. Một số thuộc tính và phương thức
- **EmployeeReportUI**:
  - `requestReportCreation()`
  - `displayReport(report: EmployeeReport)`

- **EmployeeReportController**:
  - `createReport(...)`
  - `saveReport(report: EmployeeReport, fileName: String, location: String)`

- **EmployeeReportGenerator**:
  - `generateReport()`

- **EmployeeReport**:
  - `getContent()`

- **EmployeeReportStorage**:
  - `saveReport()`

### e. Mối quan hệ giữa các lớp
- `EmployeeReportUI` gửi yêu cầu tạo hoặc lưu báo cáo đến `EmployeeReportController`.
- `EmployeeReportController` gọi `EmployeeReportGenerator` để tạo báo cáo và `EmployeeReportStorage` để lưu báo cáo.
- `EmployeeReportGenerator` trả về đối tượng `EmployeeReport` cho `EmployeeReportController`.
- `EmployeeReportStorage` lưu trữ báo cáo vào vị trí chỉ định.


### f. Biểu đồ lớp

![Class Create Employee Report](https://www.planttext.com/api/plantuml/png/V991QiCm44NtEeMM3YG-G1Ob9PHII4EewG46Use4ifJEo05JUh8kUgHUeR8jnRNLrWiRp_pvVd_ahu_F7JiWrpPQb1gOvGawibhVLeqoYXs1i_Jy8D-4x2_2rnRPFU7PajiJWbFMPAknMIa-Q-Z6PaR3Ool7rzLile0B1jbyzex8qYCoGus-zIu2LVYWDQw7GueyPOyGhV8y3suy-Synrl95QJn2WrjPE5AcNajjoo56hFn2b65_dmGBhdiqE2mgOjLZOP7n0bfLlhedvP0Kf06d-I4hckii9nMlATgc0UfIdyAp-0r6EqxM7L4E8VjeySVPRpOtoG68v4GcrNKT_ua2ebXkS5A8UPOVZHsQol-ntm000F__0m00)

#### Giải thích
- Actors: Employee
- Boundary Classes:
  - EmployeeReportUI: Giao diện để nhân viên nhập tiêu chí báo cáo. Nó thu thập thông tin từ người dùng và gửi yêu cầu đến controller.
  - EmployeeReportDisplay: Hiển thị báo cáo nhân viên sau khi được tạo.
- Control Classes:
  - EmployeeReportController: Điều phối quá trình tạo và lưu báo cáo nhân viên. Nó nhận dữ liệu từ giao diện và gọi generator để tạo báo cáo.
- Entity Classes:
  - EmployeeReportGenerator: Thực hiện logic tạo báo cáo nhân viên dựa trên tiêu chí đã nhập.
  - EmployeeReport: Đại diện cho báo cáo nhân viên được tạo.
  - EmployeeReportStorage: Chịu trách nhiệm lưu trữ báo cáo nhân viên vào vị trí chỉ định.

---

## 3. Ca sử dụng: Login

### a. Các lớp phân tích
- **Lớp Boundary**: `LoginUI`
- **Lớp Controller**: `LoginController`
- **Lớp Entities**: `User `, `AuthenticationService`

### b. Biểu đồ tuần tự
![Sequence Login](https://www.planttext.com/api/plantuml/png/R91D2i8m48NtESKiMx0Nw48KLu8hfGSOaq43CQcJYTApkV18Ni7-QGMx2VCoxtsyvFLuhg8WIxeuXLe2GnM9rJ4aRv0Rs8MJzTLMwU25WnlqPX2kDP8NAmsiavoxKQFOu0_4Dwj9gOu5K2m_c1AOhecYz3hBrNZ_jKpa4d1YKW_AKdjwlD02Qepn7jYCX2dMaMRBb713PqtBsZ2PReqkpX9dur3CLMIAoSb_XzyN6njhXys-jsP38bShygRzypS0003__mC0)


### c. Nhiệm vụ của từng lớp phân tích
- **LoginUI**: Giao diện cho người dùng nhập thông tin đăng nhập.
- **LoginController**: Kiểm tra thông tin đăng nhập và điều phối xác thực.
- **AuthenticationService**: Xử lý xác thực thông tin người dùng.

### d. Một số thuộc tính và phương thức
- **LoginUI**:
  - `requestLogin()`

- **LoginController**:
  - `authenticateUser (username: String, password: String)`

- **AuthenticationService**:
  - `validateCredentials(username: String, password: String)`

### e. Mối quan hệ giữa các lớp
- `LoginUI` gửi yêu cầu đăng nhập đến `LoginController`.
- `LoginController` gọi `AuthenticationService` để xác thực thông tin người dùng.
- `AuthenticationService` trả về kết quả xác thực cho `LoginController`, sau đó `LoginController` thông báo kết quả cho `LoginUI`.


### f. Biểu đồ lớp


![Class Login](https://www.planttext.com/api/plantuml/png/Z90n3i8m34Ntd29ZaUW5651H9oIsgWUm6gj4IXrmd7P0d8o18t45KgI8gcB0WuUlzx_y_Neygo304WUdEWSXw9FlBRL7VLDw7iPhn20VjTYekrfYjITXxnnonY7A6Kbi1u9jI7eHqoOOSASROKlzLb-IV_9iih98FNpjrbE3FDeES_O8pfgKMpEQ6G8N_atFfSfolxvShPlCpCyxL8LaqgFU0000__y30000)

#### Giải thích
- Actors: User
- Boundary Classes:
  - LoginUI: Giao diện để người dùng nhập thông tin đăng nhập. Nó thu thập thông tin từ người dùng và gửi yêu cầu đến controller.
- Control Classes:
  - LoginController: Điều phối quá trình xác thực thông tin đăng nhập. Nó nhận thông tin từ giao diện và gọi dịch vụ xác thực để kiểm tra thông tin.
- Entity Classes:
  - AuthenticationService: Xử lý logic xác thực thông tin người dùng.
  - User: Đại diện cho người dùng và thông tin liên quan đến họ.

---

## 4. Ca sử dụng: Maintain Employee Information

### a. Các lớp phân tích
- **Lớp Boundary**: `EmployeeInfoUI`
- **Lớp Controller**: `EmployeeInfoController`
- **Lớp Entities**: `Employee`, `EmployeeService`

### b. Biểu đồ tuần tự
![Sequence Maintain Employee Information](https://www.planttext.com/api/plantuml/png/V94x3i8m44Hxdy9bA7A152W8KQIWYZY0iJV8aZzXlOwKir5m9Av0285y52XSUBppTZH-tEvv884KhM52aaU-KrOxTlRHAO4jFzZQ-1QWS9K_5KnwH-ZDJDw_DGF8m96cqLG2Dbh2KcQiNyBJxGAVSOHhX40V-LGhGP1is7nkwHmJP3psbkbh0iDbZXbDKzmGEUD1D5_A2c6Ou-cVA5rPbKOhI7ltS_LA2Kg7seYsZ5922CVkYCkhX1oSwZxg2G00__y30000)

### c. Nhiệm vụ của từng lớp phân tích
- **EmployeeInfoUI**: Giao diện cho quản trị viên để xem và chỉnh sửa thông tin nhân viên.
- **EmployeeInfoController**: Nhận yêu cầu từ giao diện, xử lý và cập nhật thông tin nhân viên.
- **EmployeeService**: Xử lý các thao tác liên quan đến thông tin nhân viên.

### d. Một số thuộc tính và phương thức
- **EmployeeInfoUI**:
  - `requestEmployeeUpdate()`

- **EmployeeInfoController**:
  - `updateEmployeeInfo(employee: Employee)`

- **EmployeeService**:
  - `saveEmployee(employee: Employee)`

### e. Mối quan hệ giữa các lớp
- `EmployeeInfoUI` gửi yêu cầu cập nhật thông tin đến `EmployeeInfoController`.
- `EmployeeInfoController` gọi `EmployeeService` để lưu thông tin nhân viên.
- `EmployeeService` thực hiện lưu trữ thông tin vào cơ sở dữ liệu.


### f. Biểu đồ lớp

![Class Maintain Employee Information](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9hRa5EVcLggcTUMdwefq8rbm885AKMbgOMby0aGmjI4ajIDJIvQhcmQ7FEpoifoi_9IIs2QIy5gqTMev4AvLZ1jM8nBJYrg2mpEHLcJ75Y6TmGuWo0wKnFBN59BKdCp2a6EXfY5h88K1-QltLrxN3uYGk7Lv5rGDrDZ58kXzIy563m0m000F__0m00)

#### Giải thích
- Actors: Admin
- Boundary Classes:
  - EmployeeInfoUI: Giao diện cho quản trị viên xem và chỉnh sửa thông tin nhân viên. Nó thu thập thông tin từ người dùng và gửi yêu cầu đến controller.
- Control Classes:
  - EmployeeInfoController: Điều phối quá trình cập nhật thông tin nhân viên. Nó nhận yêu cầu từ giao diện và gọi dịch vụ để lưu thông tin.
- Entity Classes:
  - EmployeeService: Xử lý các thao tác liên quan đến thông tin nhân viên.
  - Employee: Đại diện cho thông tin nhân viên cần được cập nhật.

---

## 5. Ca sử dụng: Maintain Purchase Order

### a. Các lớp phân tích
- **Lớp Boundary**: `PurchaseOrderUI`
- **Lớp Controller**: `PurchaseOrderController`
- **Lớp Entities**: `PurchaseOrder`, `PurchaseOrderService`

### b. Biểu đồ tuần tự
![Sequence Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/Z54x3i8m3DrpYenbw0Kwe28c1WHInG5COY1IcnJ7gTIpCN0aha1RAbNzW1ZYuTdl-VdbzNYcde4u5Ba0nOxaHXV6YhCBLWFLyXX8tS3ZWJJIQIUKiqmk7-FR3vWZ2RHiU4BBa2gZSB4dHBTGnklfgaGItWDw7kEb1iPe9IRJCu71Ko93Hngr8zVMYSp0cSdrDoJIG_M7KZykur-scYmlXWfWu-nt8ql9QEFB7EeiA8NUxvi7rpQK5Arkll8D003__mC0)


### c. Nhiệm vụ của từng lớp phân tích
- **PurchaseOrderUI**: Giao diện cho quản trị viên để quản lý đơn hàng mua.
- **PurchaseOrderController**: Nhận yêu cầu từ giao diện và điều phối việc cập nhật đơn hàng.
- **PurchaseOrderService**: Xử lý các thao tác liên quan đến đơn hàng mua.

### d. Một số thuộc tính và phương thức
- **PurchaseOrderUI**:
  - `requestPurchaseOrderUpdate()`

- **PurchaseOrderController**:
  - `updatePurchaseOrder(order: PurchaseOrder)`

- **PurchaseOrderService**:
  - `savePurchaseOrder(order: PurchaseOrder)`

### e. Mối quan hệ giữa các lớp
- `PurchaseOrderUI` gửi yêu cầu cập nhật đơn hàng đến `PurchaseOrderController`.
- `PurchaseOrderController` gọi `PurchaseOrderService` để lưu thông tin đơn hàng.
- `PurchaseOrderService` thực hiện lưu trữ thông tin vào cơ sở dữ liệu.


### f. Biểu đồ lớp

![Class Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niK90QL5oHc9ngdzHIcfHgAT2DPS221Ib5fQc5fUWoXQa99QaQcXorN9Xq-oSdrTIb9-Jare4CwGKh055aKO-YBH2rOdBnE3KehBCv5IOSSM9PHGO1ZCbFRN49RKaCJEd6EWJYBd88a3Dw46Ygsk7owTSk480Gm_KByHhu798pKi1nXC0003__mC0)

#### Giải thích
- Actors: Admin
- Boundary Classes:
  - PurchaseOrderUI: Giao diện cho quản trị viên quản lý đơn hàng mua. Nó thu thập thông tin từ người dùng và gửi yêu cầu đến controller.
- Control Classes:
  - PurchaseOrderController: Điều phối quá trình cập nhật đơn hàng. Nó nhận yêu cầu từ giao diện và gọi dịch vụ để lưu thông tin đơn hàng.
- Entity Classes:
  - PurchaseOrderService: Xử lý các thao tác liên quan đến đơn hàng mua.
  - PurchaseOrder: Đại diện cho đơn hàng cần được cập nhật.

---

## 6. Ca sử dụng: Run Payroll

### a. Các lớp phân tích
- **Lớp Boundary**: `PayrollUI`
- **Lớp Controller**: `PayrollController`
- **Lớp Entities**: `Payroll`, `PayrollService`

### b. Biểu đồ tuần tự
![Sequence Run Payroll](https://www.planttext.com/api/plantuml/png/R50x3i8m3DrpYemmz08TK14J0nAYuW36CIXIce3Z87es1ex45OYWj4Lqi6G_lu_iv_rHHG6Mr3W5A87rqZJMgqD8tW2tUWij1-VsQuN1Isw_oEepEc95Ngpqr9huQf6KUZlfOZ5ub9hfaYZABlaEdCrLlnvn1_TIquqm2Vq91iv8sAMN6i5XSZ2XwoYwc8xBTnujDo0s-AcetuECZMS7RPqGASPDBZXHpgh8c_pK5m000F__0m00)

### c. Nhiệm vụ của từng lớp phân tích
- **PayrollUI**: Giao diện cho quản trị viên để khởi động quy trình trả lương.
- **PayrollController**: Nhận yêu cầu từ giao diện và điều phối việc thực hiện quy trình trả lương.
- **PayrollService**: Xử lý các thao tác liên quan đến việc tính toán và thực hiện trả lương.

### d. Một số thuộc tính và phương thức
- **PayrollUI**:
  - `requestRunPayroll()`

- **PayrollController**:
  - `executePayroll()`

- **PayrollService**:
  - `calculatePayroll()`

### e. Mối quan hệ giữa các lớp
- `PayrollUI` gửi yêu cầu khởi động quy trình trả lương đến `PayrollController`.
- `PayrollController` gọi `PayrollService` để thực hiện tính toán và xử lý trả lương.
- `PayrollService` thực hiện các thao tác cần thiết để hoàn tất quy trình trả lương.


### f. Biểu đồ lớp

![Class Run Payroll](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niK90OcLHVavEgAT2DPS221Ib5fQc5fS4bUP1fJGqkMgvK5Kxv-ULWEZK8fYkr8hKvDAILDnQWbEBoZAJKs7ganDpaajp4l7fW2bDJornIIr9pCmfXYX2k5XNrmxJHLoORaHI1tK6VaLS3gbvAS0W0W000F__0m00)

#### Giải thích
- Actors: Admin
- Boundary Classes:
  - PayrollUI: Giao diện cho quản trị viên để khởi động quy trình trả lương. Nó thu thập yêu cầu từ người dùng và gửi đến controller.
- Control Classes:
  - PayrollController: Điều phối quá trình thực hiện quy trình trả lương. Nó nhận yêu cầu từ giao diện và gọi dịch vụ để tính toán và xử lý trả lương.
- Entity Classes:
  - PayrollService: Xử lý các thao tác liên quan đến việc tính toán và thực hiện trả lương.
  - Payroll: Đại diện cho quy trình

---

