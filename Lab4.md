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


# 3. Use Case: Chạy bảng lương (Run Payroll)

Mô tả:
Tính toán và xử lý bảng lương dựa trên bảng chấm công và thông tin nhân viên.

Các bước thực hiện
+Người dùng khởi chạy quy trình tính lương.
+Hệ thống thu thập thông tin bảng chấm công và thông tin nhân viên.
+ Tính lương dựa trên các quy tắc (lương theo giờ, lương cố định, hoa hồng, v.v.).
+ Gửi lệnh thanh toán đến hệ thống ngân hàng.
+ In phiếu lương và lưu thông tin.

Lý do thiết kế:
+ Đây là chức năng cốt lõi, đảm bảo hệ thống tự động hóa quy trình phức tạp.
+ Đáp ứng các yêu cầu tích hợp với hệ thống ngân hàng và lưu trữ bảo mật.

Tương tác chính:
+ Actor: Quản lý nhân sự.
+ Boundary: PayrollForm.
+ Controller: PayrollController.
+ Entities: Timecard, Paycheck, Employee, BankSystem.


# 4. Phân tích thiết kế

1. Tính bảo mật
+ Ca sử dụng đăng nhập tập trung vào xác thực người dùng, giảm thiểu rủi ro truy cập trái phép.
+ Các dữ liệu nhạy cảm như bảng chấm công, thông tin lương, thông tin tài khoản ngân hàng được bảo vệ.
  
2. Tính mở rộng
+ Timecard và Payroll được thiết kế linh hoạt để mở rộng thêm các loại nhân viên (hợp đồng, thời vụ).
+ Hệ thống có thể tích hợp thêm các chức năng như gửi thông báo hoặc quản lý phúc lợi.
  
3. Khả năng duy trì
+ Tách biệt các lớp giao diện (Form), điều khiển (Controller), và thực thể (Entity) để dễ bảo trì và nâng cấp.



##

# 1. Use Case Diagram (Sơ đồ ca sử dụng tổng quát)

Mô tả:

  Sơ đồ ca sử dụng thể hiện các chức năng chính của hệ thống và cách các actor tương tác với các chức năng này.

Sơ đồ:

  Actors:

  + Người dùng (Nhân viên, Quản lý, Admin)
  + Hệ thống ngân hàng
  + Máy in phiếu lương
    
  Use Cases:

  + Đăng nhập (Login)
  + Duy trì bảng chấm công (Maintain Timecard)
  + Chạy bảng lương (Run Payroll)

![PlantText](https://www.planttext.com/api/plantuml/png/T991QiCm44NtEiMGLRt85KfQACsY1ZT9knVoO8dOuoB959-WwzwWQI_GRcDA5eRSmoVe5IhP3Z7OMGZ4_CVyFnhzLOU5iLpR8aiP5pRNy6HGzzVbAkJ44zJ03SmUYsR_HP3Mlq2o_YGmJVKpwz5RJjjrQIncBRjigZUmigdUAG5AF2th3qfEUAGLsRvlMEzAK0GlKZNxGm7fyVkuyoZpKM0-luQhXpnH5B1peBQwAWWYNkeyJKTQo9s3Ex1H6Ggkus3GRa8S333kVOexLbWVhPDk2YkHh1BSOi0cR3hiMU7hmFeYTnShE-I6pXqHwLoWCUSy4ymz4ceNo9U5HB6TfDP8SRj5s6XEngr9vUx5sSBL_UVu1m00__y30000)

# 2. Sequence Diagram (Sơ đồ tuần tự)
   
a. Đăng nhập (Login)

Mục tiêu: Hiển thị luồng thực hiện khi người dùng đăng nhập.

Thành phần:

- Actor: Người dùng
- Objects:
  + LoginForm: Giao diện để nhập thông tin.
  + LoginController: Xử lý logic xác thực.
  + User: Thực thể chứa thông tin người dùng.
    
- Luồng tuần tự:
  + Người dùng nhập tên đăng nhập và mật khẩu vào LoginForm.
  + LoginForm chuyển thông tin đến LoginController.
  + LoginController kiểm tra thông tin đăng nhập từ đối tượng User.
  + Trả về kết quả cho LoginForm.
  + Hiển thị kết quả trên giao diện.

![PlantText](https://www.planttext.com/api/plantuml/png/T96nYW8n48RxFCMyWDXRY21u1ugLFi0Q5mtkJZIPYDQMLbQs9rVTWOLWjIaiuela2Nm5iowokjmrmypF_Dy_8JTxQMcA59aqOH4dgM2eOyL6qk0uKcleoOd0ZbGfun99oQHGsiMGXDKOIT2wiB6yGgrPsg01_QdFZdCWzujmtLqtE04ifANxWZHq1BCW_1XMsfwCCYYGFhmz2g2fEmS6YGgELGs1yRYd0LtXxIO5Kj7_xhVJts87ocVVCFFPXM1Xydxb3ZoGl3tnlr9VN_-PH-DZUViC7xc3XCJRlQXhmtciDMEj6CVv9zm1003__mC0)

b. Duy trì bảng chấm công (Maintain Timecard)

Mục tiêu: Quản lý thông tin bảng chấm công.

Thành phần:

- Actor: Nhân viên/Quản lý
= Objects:
    + TimecardForm: Giao diện nhập liệu.
    + TimecardController: Xử lý logic.
    + Timecard: Thực thể lưu thông tin bảng chấm công.

- Luồng tuần tự:

    + Người dùng yêu cầu hiển thị bảng chấm công.
    + TimecardForm gửi yêu cầu đến TimecardController.
    + TimecardController lấy dữ liệu từ Timecard.
    + Hiển thị bảng chấm công trên giao diện.
    + Người dùng chỉnh sửa và lưu thay đổi.
    + TimecardForm gửi yêu cầu lưu đến TimecardController.
    + TimecardController cập nhật dữ liệu vào Timecard.

c. Chạy bảng lương (Run Payroll)
Mục tiêu: Tự động tính toán và xử lý bảng lương.

Thành phần:

Actor: Quản lý
Objects:
PayrollForm: Giao diện chạy bảng lương.
PayrollController: Xử lý logic tính toán.
Timecard: Lấy dữ liệu giờ làm việc.
Employee: Thông tin nhân viên.
Paycheck: Tính toán và lưu lương.
BankSystem: Gửi lệnh thanh toán.
Luồng tuần tự:

Quản lý yêu cầu chạy bảng lương trên PayrollForm.
PayrollForm chuyển yêu cầu đến PayrollController.
PayrollController lấy dữ liệu từ Timecard và Employee.
Tính toán lương, lưu kết quả vào Paycheck.
Gửi lệnh thanh toán đến BankSystem.
Hiển thị xác nhận thành công.

# 3. Class Diagram (Sơ đồ lớp)
Các lớp chính:

+ User: Lớp chứa thông tin người dùng.
+ Timecard: Lớp đại diện bảng chấm công.
+ Employee: Thông tin nhân viên.
+ Paycheck: Thông tin phiếu lương.
+ BankSystem: Hệ thống xử lý thanh toán.

Quan hệ giữa các lớp:
+ Employee sở hữu Timecard.
+ PayrollController xử lý tính toán và tương tác với Paycheck.
+ Paycheck kết nối với BankSystem để thực hiện thanh toán.

  
![PlantText](https://www.planttext.com/api/plantuml/png/V9AnJiCm48PtFuNLgGmTM3DLI0niIALYliRND8hjY-uSgWZnP0my4g-0ayOceHLURFtw_-_kR7z_Vcqb08VEMLLQ4D5xGTRlIW-hYsSF3WijWMjVNTGssix4PgbQgcg_lYlqWSYg3pNXNcg79R19I7IjfHxnASPh7oxYYJgML-86etgq19FUjGO29iG0VwFQ_C8V9zY_yEi112nmlwXKOTYDwb3aekSgpz2N9ooRL0KSTJxyYNlas6goNhVw0BxPzHBG9KpBLA98Z3ZqORsWpkBZUwpkLtgp6RTyeOMcinULx-2s9pvK8vgyobFCV3bRv0cCFXBVDCycA5BpqNxerHQz6JxG3m000F__0m00)
