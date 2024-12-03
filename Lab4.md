# 1. Use Case: Đăng nhập (Login)
Mô tả:
Cho phép người dùng truy cập hệ thống bằng cách nhập tên đăng nhập và mật khẩu.

Các bước thực hiện:
+ Người dùng nhập tên đăng nhập và mật khẩu.
+ Hệ thống kiểm tra thông tin đăng nhập.
+ Nếu thông tin đúng, chuyển đến trang chính; nếu sai, hiển thị lỗi.
  
Lý do thiết kế:
+ Đảm bảo hệ thống chỉ cho phép người dùng hợp lệ truy cập, tăng cường tính bảo mật.
+ Yêu cầu chức năng cơ bản để bất kỳ hệ thống nào cũng có thể bảo vệ dữ liệu nhạy cảm.
  
Tương tác chính:
+ Actor: Người dùng.
+ Boundary: LoginForm.
+ Controller: LoginController.
+ Entity: User.


# 2. Use Case: Duy trì bảng chấm công (Maintain Timecard)

Mô tả:
Người dùng có thể thêm, sửa, hoặc xem thông tin bảng chấm công.

Các bước thực hiện:
+ Người dùng chọn bảng chấm công cần chỉnh sửa.
+ Hệ thống hiển thị thông tin bảng chấm công hiện tại.
+ Người dùng cập nhật thông tin (giờ làm việc, mã dự án, v.v.).
+ Hệ thống lưu lại thay đổi.
  
Lý do thiết kế:
+ Cho phép nhân viên và quản lý ghi lại thời gian làm việc, hỗ trợ việc tính lương chính xác.
+ Hệ thống linh hoạt để chỉnh sửa dữ liệu khi có sai sót.
  
Tương tác chính:
+ Actor: Nhân viên, quản lý.
+ Boundary: TimecardForm.
+ Controller: TimecardController.
+ Entity: Timecard.
