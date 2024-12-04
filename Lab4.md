# Thiết kế các ca sử dụng hệ thống Payroll System
# Các ca sử dụng hệ thống "Payroll System"
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
 
![PlantText](https://www.planttext.com/api/plantuml/png/d98_IiH05CRxESLt0IzW8GiBQcKL2yliPCW6ve-ydLasjOM5Pn044K5OjB3A51O1xp4dy0g-g9W4ih9Opl1-l_VnyJxYsspbS_B1Q95BxmZdAqLYuO8jSggHLKR9d8fZHqP8Ppqv_Viv_tvh1fJrbU_7XUWqE3WQ2N28Y_OfGARcCM2Z31QfkRSbv38r3mQoVRMb6143Gx-DFISfRYlKlKspeKQHuZDqbU9r41FSmCQEZ4ADJM3G3y4_G-qCb15JUskcC_rqTChybOLVfdWpQTdHxHdFR2zHCduBtTuPhBiayh-Dlh_iKUByQwVjLezQ56AcRD6TrIS0003__mC0)

c. Chạy bảng lương (Run Payroll)

Mục tiêu: Tự động tính toán và xử lý bảng lương.

Thành phần:

- Actor: Quản lý
- Objects:
    + PayrollForm: Giao diện chạy bảng lương.
    + PayrollController: Xử lý logic tính toán.
    + Timecard: Lấy dữ liệu giờ làm việc.
    + Employee: Thông tin nhân viên.
    + Paycheck: Tính toán và lưu lương.
    + BankSystem: Gửi lệnh thanh toán.
    
- Luồng tuần tự:

    + Quản lý yêu cầu chạy bảng lương trên PayrollForm.
    + PayrollForm chuyển yêu cầu đến PayrollController.
    + PayrollController lấy dữ liệu từ Timecard và Employee.
    + Tính toán lương, lưu kết quả vào Paycheck.
    + Gửi lệnh thanh toán đến BankSystem.
    + Hiển thị xác nhận thành công.

![PlantText](https://www.planttext.com/api/plantuml/png/V9A_IWGn4CRxFCMyW2zW8OUYNg4WUerbBXisosKdailAfRQmy1c4MqM4WqCBgrt48d3laIVm5Pn5Shk5PpFX6-RxpH_otNwDvevRLvMQSU6CXV7bEKUUIykcfiACMmyNt5kZzOcn9HC67OcKE_gLciebki9vc1Ib5DncIH-NDzfuAPCcer1Ip98-v3YxydCdIyQslM7lODWLzk4wh2eGiNcbg69JUvZ6vXbpq9ltJOqv6vRtxdu-Ofp6Tbs0xqaBIe0EdpjO0pCHqs84EelDYuSijc-WYzZULv3JyqYePGctNKRypKZ7s3AS2X_Ks1K8gC8JaZkiy6zpkXoP9s6D2fm9DVu_T7_TxVwQnklCYYV4pdQ3-uzfgpiaLsmVO15gGVF6PesWJ5XsUOgAiP74hFjBFm000F__0m00)

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
