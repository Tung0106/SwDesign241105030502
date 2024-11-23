# 1. Maintain Timecard
- **Tên ca sử dụng**: Maintain Timecard
- **Mô tả**: Người dùng (nhân viên hoặc quản lý) có thể thêm, sửa đổi hoặc xóa thông tin về thời gian làm việc của nhân viên.
- **Người tham gia**: Nhân viên, Quản lý
- **Tiền điều kiện**: Người dùng đã đăng nhập vào hệ thống.
- **Luồng sự kiện chính**:
  - Người dùng chọn chức năng "Maintain Timecard".
  - Hệ thống hiển thị danh sách thời gian làm việc hiện tại.
  - Người dùng chọn thêm, sửa đổi hoặc xóa một thời gian làm việc.
  - Hệ thống yêu cầu thông tin cần thiết.
  - Người dùng nhập thông tin và xác nhận.
  - Hệ thống lưu thay đổi vào cơ sở dữ liệu.
- **Hậu điều kiện**:
  - Thông tin thời gian làm việc của nhân viên đã được cập nhật thành công trong cơ sở dữ liệu.
  - Nếu có thêm, sửa đổi hoặc xóa, hệ thống phản ánh chính xác trạng thái mới của thời gian làm việc.
  - Người dùng nhận được thông báo xác nhận về việc thay đổi đã được thực hiện.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/T94nImCn7CNtV8f7T-dUGGek3kfY7Hp_veucSCaTbrnfPmS7SN1m57kJK2WAEbs63f5-Ztm2luA9LQYM3bdU_xttUv1FjneQIxLjLC68sxB6XSbhLaL9SbcHjZYV6Pihnj81E3Zy4GOu4i7TQVHEIMeR7qPIvPpghCSsbcHEgG6EPN3N6ZOcRf6H5Z2-vU9RU9GOIz8e_5nX4eqtV2_B2hzGVHFSalfJ_qPx2_uFkFIB1ZnqpqtgUDTZs3Wu2QbKXcvbTw5d8dJBQZimyNDCutBeTD9RcD_CoVer8MY6Z_lW7cIAbE3h5d7r4xBWNb2aZStEnj66S-NRyWzacEii_iyN0000__y30000)

# 2. Login
- **Tên ca sử dụng**: Login
- **Mô tả**: Người dùng có thể đăng nhập vào hệ thống bằng thông tin tài khoản của mình.
- **Người tham gia**: Người dùng
- **Tiền điều kiện**: Không có.
- **Luồng sự kiện chính**:
  - Người dùng mở trang đăng nhập.
  - Người dùng nhập tên đăng nhập và mật khẩu.
  - Hệ thống xác thực thông tin đăng nhập.
  - Nếu thông tin hợp lệ, người dùng được chuyển đến giao diện chính; nếu không, thông báo lỗi được hiển thị.
- **Hậu điều kiện**:
  - Nếu đăng nhập thành công, người dùng đã được chuyển đến giao diện chính của hệ thống.
  - Nếu đăng nhập không thành công, người dùng vẫn ở trên trang đăng nhập và nhận được thông báo lỗi.
  - Thông tin đăng nhập của người dùng được ghi nhận trong phiên làm việc hiện tại.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/X90nJWCn44NxESM_01T8WIBHq423a6YDOyLMTcTNkxEHKgUWI1CgIf8If1H8L76HmdiHdu0hO8SWGYXmuHbz___qvG-_6xQY6kdAWfIMgi5jQngga-IqgnKBRcQjc98eFm1dvmTXWAledo6DuZ7wntwU1jkutTH_dTTx7H9U-RSLqx12cJR190al7Nr5ZiDtOQqXDlgtFC9x2eixuP0g1Ftoc9oiAxRGEK18vuUS-mrmORjPzFDCYjiTO-nKXP6B_e6XRTYm9LEqvWGxEJJuZtxfzkpSU_5T-pwiAnJHFpaoFA9XkjA_Vm800F__0m00)

# 3. Run Payroll
- **Tên ca sử dụng**: Run Payroll
- **Mô tả**: Hệ thống thực hiện tính toán và xử lý lương cho tất cả nhân viên.
- **Người tham gia**: Quản lý
- **Tiền điều kiện**: Người dùng đã đăng nhập và có quyền truy cập.
- **Luồng sự kiện chính**:
  - Người dùng chọn chức năng "Run Payroll".
  - Hệ thống kiểm tra thời gian làm việc và thông tin lương.
  - Hệ thống tính toán lương cho từng nhân viên.
  - Hệ thống lưu kết quả vào cơ sở dữ liệu và gửi thông báo cho người dùng.
- **Hậu điều kiện**:
  - Lương của tất cả nhân viên đã được tính toán và lưu trữ trong cơ sở dữ liệu.
  - Các thông báo về kết quả thanh toán đã được gửi đến người dùng (quản lý).
  - Hệ thống ghi nhận thông tin về các giao dịch lương đã thực hiện.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/R90nJWCn44Lxd-8hFHT8WI9Hf00a15p0EAjT2-yuUCUHKbEauWY8B7IWY1HKSP72qjx39-0AE691MwGRpPl_vyzyX_saOUdOrqP8nTRXKf8i2oVckQkLdajYt2mRBceXUeQJqxurnbcLmXDXTEq9LtBfh34ZyGk7O-SwXSSQx2GuAvurIYq99gvhB39RAIpYEhFuHILOPzHjkvRA8rwtSKCLsCRsVmggik0KFd99LNobR1hVwOZuejjwtAVTdl7Wq-xjiDP2TIsQ55umI-4JvX383yJztMDCKzZelvHtiRL3Ap4fQ9OV-GC00F__0m00)

# 4. Banksystem Subsystem
- **Tên ca sử dụng**: Access Bank System
- **Mô tả**: Hệ thống kết nối và thực hiện các giao dịch với ngân hàng.
- **Người tham gia**: Quản lý
- **Tiền điều kiện**: Người dùng đã đăng nhập và có quyền truy cập.
- **Luồng sự kiện chính**:
  - Người dùng chọn chức năng "Access Bank System".
  - Hệ thống yêu cầu thông tin giao dịch.
  - Người dùng nhập thông tin và xác nhận.
  - Hệ thống gửi yêu cầu đến ngân hàng và nhận phản hồi.
  - Hệ thống hiển thị kết quả giao dịch cho người dùng.
- **Hậu điều kiện**:
  - Giao dịch với ngân hàng đã được thực hiện thành công và thông tin phản hồi từ ngân hàng được ghi nhận.
  - Nếu giao dịch không thành công, hệ thống hiển thị thông báo lỗi và không thay đổi trạng thái hiện tại của dữ liệu.
  - Người dùng nhận được thông báo về kết quả giao dịch.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/T90z2i9058JxFSLWxmLIY3-5DefWPRci8LdKPqmsehMbM7a1nK8GxAooXKLEiYVm2cvYm0HYjJ3lcpVpzgrVxKZnKCNB1UD2hK8CEN7F3LbWLIbam4bXiekKkwn8NKvpnWeOpLR1EEZvHXy9ZOuGRXJbN35hiE-RqONHmJIznn0ckSLGVlea3qeIFCbNc1bz47vTniWtoICe6pRf6Tlq8a3PY4f9MG47VQCV4hjVM3aXxrXQFxOxhWHxo4bYRfANmZgsKiLKSyj06hqdMyiIVtrjbsRsjpy0003__mC0)


# 5. Printservice Subsystem
- **Tên ca sử dụng**: Print Documents
- **Mô tả**: Hệ thống cho phép người dùng in các tài liệu liên quan đến lương và thời gian làm việc.
- **Người tham gia**: Quản lý, Nhân viên
- **Tiền điều kiện**: Người dùng đã đăng nhập và có quyền truy cập.
- **Luồng sự kiện chính**:
  - Người dùng chọn chức năng "Print Documents".
  - Hệ thống hiển thị các tài liệu có thể in.
  - Người dùng chọn tài liệu và định dạng in.
  - Hệ thống gửi yêu cầu in đến máy in.
  - Hệ thống thông báo cho người dùng khi in hoàn tất.
- **Hậu điều kiện**:
  - Tài liệu đã được gửi đến máy in và quá trình in đã được hoàn tất.
  - Nếu in không thành công, hệ thống hiển thị thông báo lỗi cho người dùng.
  - Người dùng có thể nhận được thông báo xác nhận về việc in thành công.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/T90nRi9044NxFSKNVIxW8a9A958Y9Jc0irZi2Zn6zZWADKMAY88Rs0L2YaILL7P1iLnaJv0hP9POYX6Y_VF-l9tzQG_3WkESotIkOirPZkSYoTL28glj8YR6uxBW93sBnhab5am56BYvxQ08TyQtQyBWHE0-qsMQ41S3zGS4D7GYF5ZVhWWi_0UqgpNOLHPpYTzB2RvEenKiNPNq2w-kmd4ZkyXWufkQfg7vB-rU767asxt5qdsAn3UxCc3TiAzuCkvRThouEiFCMA5WCbU9r3TRlhYcZx-5OyZuPazgcD14llON003__mC0)

# 6. ProjectManagerDatabase Subsystem
- **Tên ca sử dụng**: Access Project Management Database
- **Mô tả**: Hệ thống cho phép người dùng truy cập và quản lý thông tin dự án.
- **Người tham gia**: Quản lý
- **Tiền điều kiện**: Người dùng đã đăng nhập và có quyền truy cập.
- **Luồng sự kiện chính**:
  - Người dùng chọn chức năng "Access Project Management Database".
  - Hệ thống hiển thị danh sách các dự án hiện có.
  - Người dùng có thể thêm, sửa đổi hoặc xóa thông tin dự án.
  - Hệ thống lưu thay đổi vào cơ sở dữ liệu và thông báo cho người dùng.
- **Hậu điều kiện**:
  - Thông tin dự án đã được cập nhật thành công trong cơ sở dữ liệu.
  - Nếu có thêm, sửa đổi hoặc xóa, hệ thống phản ánh chính xác trạng thái mới của thông tin dự án.
  - Người dùng nhận được thông báo xác nhận về việc thay đổi đã được thực hiện.
- **Biểu đồ sequence**

  ![Diagram](https://www.planttext.com/api/plantuml/png/R90nJWCn44Lxd-8hFKgV0WL1GG4I4hd0n6l5HjdPQEr5IKr1WIWeg65Rf0WGLBYWCCezV0AkmAooA4sQAMRytl_oR_mU-q1rQCgv8Xsg6kV4D3ErMiZMQRSW3hXS-M1AfVeR3WxxrGZ7DiTxnk18Q-CzBkhgokZGMqeZy0a5cf8t0xLbEheNZN3gShnX1B7SeI2syAdL5becYXpVaLhUbpknwQKS-XpND5oc3n95-kGPWkCTjmlynyusRuqyfHL-7d9yTBXEpnNqfeMedZho5NFfTDliQplPPanJMs7PDMIRlzQineOB-S4_0000__y30000)
