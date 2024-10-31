# ***Phân tích kiến trúc và ca sử dụng hệ thống `Payroll System`***

1. **Phân tích Kiến trúc**

    - **Kiến trúc lựa chọn**: Kiến trúc MVC chia hệ thống thành ba phần chính: Model, View, và Controller. Mỗi thành phần có vai trò và nhiệm vụ riêng, giúp phân tách rõ ràng giữa dữ liệu, giao diện và xử lý logic nghiệp vụ, tạo ra hệ thống dễ bảo trì, mở rộng và nâng cao tính linh hoạt.
    - **Các thành phần MVC**:
      + **Model**: Quản lý dữ liệu và logic nghiệp vụ cốt lõi (thông tin nhân viên, thẻ chấm công, và phiếu lương). Model sẽ liên kết với cơ sở dữ liệu để lưu trữ và truy xuất thông tin cần thiết cho quá trình tính lương.

      + **View**: Chịu trách nhiệm hiển thị giao diện người dùng để nhân viên và quản trị viên nhập liệu, xem báo cáo, và kiểm tra trạng thái thẻ chấm công.

      + **Controller**: Nhận yêu cầu từ người dùng, điều hướng giữa View và Model, và cập nhật các thay đổi lên giao diện dựa trên dữ liệu từ Model.
   - **Biểu đồ package mô tả kiến trúc**:
             ![Diagram](https://www.planttext.com/api/plantuml/png/R95D3i8W44Rtd88Bz0gcYRfiDD6u7s5Y6mTeWAPfZ2TpuP6yWltHWjW5YycRUHy3hySpTnwiRnGnLeEumWNvscXl3H5QVcES2mBd-5RLP3h406Tqh1GAi781xQ5Jg7r4xY6dC19f8U9FdEf2tLXHWiETbR_gKuNjWda3hZoRs7X0Gk4_tc5g9WLKslVdUuaHzX7HwsJPQbg2ZNb36MsQD8xpqyf98sCvQZbymHi00F__0m00)

2. **Cơ chế phân tích**
  - **Persistency (Lưu trữ lâu dài)**:
    - Mô tả: Hệ thống cần có cơ chế để đảm bảo dữ liệu như thông tin nhân viên, bảng lương và các dữ liệu liên quan được lưu trữ an toàn và tồn tại lâu dài, ngay cả khi ứng dụng tắt.
    - Lý do: Để đảm bảo rằng dữ liệu quan trọng không bị mất và có thể được truy xuất khi cần thiết.
  - **Distribution (Phân phối)**:
    - Mô tả: Hệ thống sẽ phân phối logic nghiệp vụ trên nhiều nút trong hệ thống, cho phép xử lý đồng thời.
    - Lý do: Điều này giúp tăng tốc độ xử lý tính toán lương cho nhiều nhân viên, giảm thiểu quá tải cho một máy chủ duy nhất và nâng cao hiệu suất tổng thể.
  - **Security (Bảo mật)**:
    - Mô tả: Cần thiết lập các biện pháp bảo mật để chỉ những nhân viên có quyền mới có thể truy cập và chỉnh sửa thông tin cá nhân của họ và thông tin nhạy cảm như bảng lương.
    - Lý do: Để bảo vệ dữ liệu nhạy cảm khỏi truy cập trái phép, đảm bảo rằng chỉ những người dùng hợp lệ mới có quyền thao tác trên thông tin cá nhân.
  - **Legacy Interface (Giao diện hệ thống kế thừa)**:
    - Mô tả: Hệ thống mới cần có khả năng giao tiếp với hệ thống quản lý dự án hiện có mà công ty không muốn thay thế.
    - Lý do: Để duy trì tính tương thích và tích hợp với các hệ thống cũ, cần có một giao diện chắc chắn giữa hệ thống mới và cũ nhằm đảm bảo dữ liệu được truyền tải đúng và đầy đủ.
  - **Data Validation (Kiểm tra tính hợp lệ dữ liệu)**:
    - Mô tả: Cần có cơ chế để kiểm tra tính hợp lệ của thông tin đầu vào từ người dùng, như thông tin ngân hàng và bảng chấm công.
    - Lý do: Để tránh lỗi và đảm bảo rằng thông tin được nhập vào hệ thống là chính xác, từ đó cải thiện chất lượng dữ liệu và giảm thiểu rủi ro trong xử lý thanh toán.
  - **Audit Logging (Ghi nhật ký kiểm tra)**:
    - Mô tả: Hệ thống cần ghi lại các hành động quan trọng liên quan đến dữ liệu nhạy cảm, như cập nhật thông tin nhân viên hoặc thay đổi phương thức thanh toán.
    - Lý do: Để có thể theo dõi và truy cứu lại các thay đổi trong hệ thống, tăng cường tính minh bạch và phát hiện các hành vi đáng ngờ.
3. **Phân tích ca sử dụng Select Payment**
 - **Các lớp phân tích của ca sử dụng Payment**:
    - Entity:
      - Employee: Lưu thông tin cơ bản của nhân viên, như tên, ID, và phương thức thanh toán.
      - PaymentMethod: Lưu trữ chi tiết phương thức thanh toán (gửi qua thư, nhận tại chỗ, hoặc chuyển khoản trực tiếp).
      - PayrollRecord: Lưu thông tin về kỳ lương, số tiền thanh toán, ngày thanh toán.
    - Boundary:
      - PaymentUI: Giao diện cho nhân viên lựa chọn hoặc xác nhận phương thức thanh toán.
    - Control:
      - PaymentController: Điều phối các thao tác trong quá trình thanh toán, lấy thông tin từ Employee và PaymentMethod, xử lý yêu cầu thanh toán, và cập nhật trạng thái thanh toán trong PayrollRecord.
- **Biểu đồ sequence**:
    ![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9hRa5EVcLgAbTIVcbUIc9HfK90OcLkQbv9g2TNSdvUIL5-3ap46SBDIItY0l8oIy1AGG91gSdvHIbSN32p57Jj4AOeM2aaPppStPkdK91nRCEnXNdf2YL0_ifa89MObw5GadzuOHuNGZb2By8-e1df3tUlpIJ622HTGAFWJh9Io7cuQsabKCVXBI3zcNaAUHc75-Kfb6KUNeL3CrJGDxKa8py5RWB9Ra099L1mFDorjW1eEv0gGNOF0ODGVGFLbtHuOJwgWNYS1zAq0CX91cdbSaZDIm6b0m00003__mC0)
  
- **Biểu đồ lớp**:
  
   ![Diagram](https://www.planttext.com/api/plantuml/png/Z5CnQiCm5DrzYa-cjf3GhgAKGDCXGw2qpG4K-vE8o9AGv41eE_G8EKA6JYNGEHuojEGUFa6lKDanjjKO6WqM-l-zh_V_at_INTzOgcqIyo3ar1YuYnMNIqHu3i2jBc0P64O47grcObec18tnJqZHPOp2Zj3Ef8FVDu_1Qn3GYR6QXXOETtdvwiAuE3ujLLtTKKi62-TZLK818kHiWVfGuEoSm4Aog4QFAEEdOWTCOsW7gAHXzbIIQq1BpXymbBfkG1sYHmEZiKo49H39PCBH7zc0MjTk_lMgvwdni99Za3kHtjXQHUNfMobiBWDrHLTQXcXC2MWoAzSxLnteTelDTuU0oT8DH5dwBgPm4_ZPwnT7AiqXCC-sEx2pBFsWRRZ2bdzHlY6jy4QBbUvUxw9JFs82tokMfMy9ACTSiLfu2_UouFgU4WYpxKQ1cBdDrdHdol6e6ZK9sFtdVkr6PR_MeUFrKKJvN_OB003__mC0)
    - **Giải thích**:
      - Employee:Lớp đại diện cho nhân viên, với thuộc tính lưu trữ ID, tên và phương thức thanh toán.
      - Lớp cha trừu tượng cho các phương thức thanh toán khác nhau (PickUp, Mail, DirectDeposit).
      - Các lớp con kế thừa từ PaymentMethod, mỗi lớp đại diện cho một phương thức thanh toán cụ thể.
      - Lớp lưu trữ thông tin về kỳ lương, số tiền thanh toán và ngày thanh toán.
      - Lớp giao diện người dùng cho phép nhân viên chọn phương thức thanh toán.
      - Lớp điều phối các thao tác trong quá trình thanh toán, bao gồm việc lấy thông tin từ nhân viên và cập nhật thông tin thanh toán.
     


4. **Phân tích ca sử dụng Maintain Timecard**
- **Xác định các lớp phân tích**
  - **Employee**: Đại diện cho nhân viên sử dụng hệ thống để nhập giờ làm việc.
  - **Timecard**: Đối tượng ghi lại số giờ làm việc của nhân viên trong một khoảng thời gian cụ thể.
  - **Project Management Database**: Hệ thống cơ sở dữ liệu để lấy các mã dự án mà nhân viên ghi lại giờ làm việc.
  - **Payroll System**: Hệ thống thực hiện các tác vụ liên quan đến bảng chấm công và trả lương.3
- **Biểu đồ sequence**:
![Diagram](https://www.planttext.com/api/plantuml/png/Z5D1IWCn5Dtd5Fy2lO0BAQWB5q91FK0c4sP69ab9CwMp51SkN7a0iKCfWb1GS3L1N8pq7Zc1L_37TknCxM1t-J__lV_o_i-N_UYF3DKc4ocXp2WD9sAOgfnp4gXCXbJdS948pgWEBqy9Kz9ebVwcZbPnoZNXqYHcKqn2QcX0Hnm6MbrnPiwef14NM7QylgaX0vfxZlDyPBWWf1O0lSD6QpW0uUmZH0bL42REtaemTQz6MGEq4OVWl7hEWBdoAGDHpI1qzXMgGf8TnKZHgHcPKbVEypP9TtclIu_Hhfp1sDdh__Li6n7Zys_m-R6pTsrqjtaoTkLYY9ZgJKRed4GddNs0j9eA67i_sJusHiukalrOsexMMM_WyYLhKlmPuzOickknIyBdFTe14qoZZdTFlonaHDgupa5CgeAjt95-Fz2Zdy10W0F23WoZkG3cs-qrdRMoe2eKdd5RZU-0sQcCrpHzBaF_uxu1003__mC0)
- **Biểu đồ lớp**:
  ![Diagram](https://www.planttext.com/api/plantuml/png/Z9FDIiD04CVlVOeXfogqs6kGKgWA1GMX5S_RP4XNazsu7yKW7do4Fe4Kpw9dWtYez3to1Bw22TbDAx4VEInaPdx_dVym-vD-zQGYGkaeR7WXaH9EepZa2I8yD23_Me0cCF1T62f1MM0IZ4HOXHuRXX_H23qY_8fN9b3ZDmh7Wj-WfsfndwZymfFyD849rq9USt6BUQdFzJZ4LIENfSe5OIJ029dAGJ8cqZe3252PeZxtKJOFN3YdKXsNbtRNf4WYU1WE4wamgl2yJG-bj8QRrgXRpI0Nd7BgruTpDQXKV2hZa2GsSyP5rBHSMK5Ph9ND5oQAlFslQ_SvKqMtAFOsMbP9CiKzp9XYFOwe6d4pcktcgvroEWwqMk0SjTk7pcfLN91P-WoJB7tJq6tyuyI27MTzXYvypsYMFcc8StP6TxARTy85jNnVpba0QZ7tTWlzsGWNxhFq5SB5vtQmPljEPnylp80zP7xn3dy1003__mC0)
   - **Giải thích**:
    - Employee: Đại diện cho nhân viên sử dụng hệ thống, có các thuộc tính như employeeId và name.
    - Timecard: Lưu thông tin về thời gian làm việc của nhân viên cho một dự án cụ thể, bao gồm mã dự án (projectId), ngày (date), và số giờ làm việc (hoursWorked).
    - ProjectManagementDatabase: Hệ thống cơ sở dữ liệu để lấy danh sách mã dự án.
    - PayrollSystem: Hệ thống xử lý bảng chấm công và trả lương, với phương thức xử lý processTimecard.
    - TimecardUI: Giao diện để nhân viên nhập thông tin giờ làm việc.
    - TimecardController: Điều phối các tác vụ duy trì thông tin timecard, như lấy mã dự án, lưu thông tin, và gửi thông tin đến hệ thống bảng chấm công.
 5. **Hợp nhất kết quả phân tích**
      # Tài liệu Mô tả Hệ thống Quản lý Chấm công và Thanh toán
      1. **Tổng quan**
          - Hệ thống này cho phép nhân viên quản lý thẻ chấm công và chọn phương thức thanh toán. Các ca sử dụng "Select Payment" và "Maintain Timecard" cung cấp chức năng cho nhân viên lựa chọn phương thức nhận lương và ghi lại giờ làm việc. Hệ thống tuân theo mô hình kiến trúc MVC (Model-View-Controller) để đảm bảo tính rõ ràng và dễ dàng mở rộng.
      2. **Các lớp phân tích**.
       - **Lớp Entity (Mô hình - Model)**
         - Employee: Lưu thông tin cơ bản của nhân viên, như tên, ID, và phương thức thanh toán đã lựa chọn.
         - Thuộc tính chính: employeeId, name, paymentMethod
         - PaymentMethod: Lưu trữ chi tiết về các phương thức thanh toán, là lớp cha của các lớp con như PickUp, Mail, và DirectDeposit.
         - Thuộc tính chính: methodType
         - PayrollRecord: Ghi lại kỳ lương, số tiền thanh toán và ngày thanh toán.
         - Thuộc tính chính: recordId, amount, paymentDate
         - Timecard: Ghi lại số giờ làm việc của nhân viên trong một khoảng thời gian cụ thể.
         - Thuộc tính chính: timecardId, employeeId, projectId, date, hoursWorked
         - ProjectManagementDatabase: Hệ thống cơ sở dữ liệu quản lý mã dự án cho phép nhân viên ghi nhận giờ làm việc.
         - Phương thức: getProjectCodes()
      - **Lớp Boundary (Giao diện - View)**
         - PaymentUI: Giao diện cho phép nhân viên lựa chọn hoặc xác nhận phương thức thanh toán.
         - TimecardUI: Giao diện cho nhân viên nhập thông tin giờ làm việc vào hệ thống.
      - **Lớp Control (Điều khiển - Controller)**
         - PaymentController: Điều phối các thao tác trong quá trình thanh toán, lấy thông tin từ Employee và PaymentMethod, xử lý yêu cầu thanh toán và cập nhật trạng thái thanh toán vào PayrollRecord.
         - TimecardController: Quản lý luồng nhập thông tin giờ làm việc của nhân viên, lấy mã dự án từ ProjectManagementDatabase, lưu thông tin vào Timecard, và gửi yêu cầu xử lý lương.
      - **Biểu đồ sequence hợp nhất**
         ![Diagram](https://www.planttext.com/api/plantuml/png/Z5HDIiD05Dxd5Ey2lO1G4TI52w7uSu3fP4WZcPcIJ8fPYWjNBZo0Q10H1Q62gmPn4UazvWHUmVUQfabgebqaOTwyzyttVUzDlhFFdSYmqCGoS1WtEeHzEGvq8eGprB5oMPZ0W2LIA7DwK8LEV2au2rsCSQrCg8CoQxTO1Y9SxPJ9jIrCz4q5KwuHWnAE1DSOT9bXGnO968JwJ71po1Jp11sojznPgpjE8YEau_Jx9HigvIAAeDztIc7GswuamHRmaSsk5On7y-ayLHuON3zp_30r0gFpL3bLUbLRgK6Cyppbe4PszheHKAss0AnK8rWmdyPObRyJXgys1YZaaoBaCIxe632XdHLiyjHVnwgLzVwNjd3saFdAuBDgNfV7rOmWYhJP7NW-q-3wDhj2KMNhQscreWQ597-9ITHJ339_0DTcRq02Mf99HDUqaBLszfWqGRhJUrryoD87cDZieWdLBN_XtxZUL0zjk8KWlvSm8KVu9aPuDdlrDqDfUhBgLSjqhJVYxzdwHU7hncQNS8vXvF51y3JyBSFLggX-SHfZEqIByGIydBD72PoEQsMuxlIIsJ1FDGqxlkW4ZDxZt1SmEqAvzB_x0G00__y30000)
      - **Biểu đồ lớp hợp nhất**
         ![Diagram](https://www.planttext.com/api/plantuml/png/Z5J1Jjmm4BtdAwmzRIijAjS88IGM9AIkgCgYdht9i1XYZsLFK2FKB-k1J-elr4bi9zwGXHmIUVpyvisRZF_zVRkmn0tLiigAYblBhgIki05Whnbppug13zoKERiZ8zJURoWkuI2aUID1qGRe4HtyntYP_SbyYYGSyyXkkMtqG3gS4CNplMRmcq2L1mGUik6YEWfO2mC5hK6Z5JI370GQhAgVKA0P19fkER61IwmLvQp4UbT1QiIQawkcVG-rR8M4WezuoGScpBFEQuDFhfP9l1pIzO57h8tzXUOPoYXmCBLdsN35z-3LyXsteVMCxO4yw19BiCilEVikB9trIS-JZhQ6tJMMGCRZJcO1rdgBbxr_UUgketn1CVqvxcyYJIcihdZZDsur2LITbkvWZobGFGWZGwe9Qp1zIXjshj780rAXT4rXlpMdtG_hYU9BLDJM1IQc44gGSDq8ia93ypXbQS9QbpswvVcaNq7FE-a_Qb-Film50iao_8j3dQb2M--ae2q6ZVDu9p1U9OlJ1LkjkaywR-bD464d9ryNVkQFGjgPFmf8PdwgvrkVQEpl72Ys_Hs_n-NDpTH7vyO3b5sugwczaVy3003__mC0)
      3. **Mô tả ca sử dụng**
    - **Ca Sử dụng: Select Payment**
        + Luồng hoạt động:
            - `Employee` yêu cầu `EmployeeController` hiển thị danh sách các phương thức thanh toán có sẵn.
            - `EmployeeController` yêu cầu `EmployeeView` hiển thị danh sách các phương thức thanh toán từ `PaymentMethod.`
            - `Employee` chọn phương thức thanh toán mong muốn từ `EmployeeView.`
            - `EmployeeController` cập nhật thông tin `Employee` với phương thức thanh toán mới trong `Model`.
            - `EmployeeView` hiển thị thông báo xác nhận cập nhật thành công.

        + Mục tiêu: Nhân viên có thể lựa chọn và cập nhật phương thức thanh toán mong muốn thông qua hệ thống.

    - **Ca Sử dụng: Maintain Timecard**
        + Luồng hoạt động: 
            - `Employee` yêu cầu `TimecardController` mở thẻ chấm công hiện tại.
            - `TimecardController` lấy thông tin `Timecard` từ `Model` và hiển thị qua `TimecardView`.
            - `Employee` nhập thời gian làm việc và các mã số dự án liên quan vào `TimecardView`.
            - `TimecardController` xác nhận thông tin và cập nhật dữ liệu vào `Timecard` trong `Model`.
            - `TimecardView` hiển thị thông báo xác nhận rằng thẻ chấm công đã được cập nhật.
        
        + Mục tiêu: Nhân viên có thể quản lý và cập nhật thông tin chấm công của mình một cách chính xác.

# ---------------------- HẾT ----------------------------------
