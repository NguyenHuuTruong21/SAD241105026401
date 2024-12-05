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

   
1. Đăng nhập (Login)

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


2. Duy trì bảng chấm công (Maintain Timecard)

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


3. Chạy bảng lương (Run Payroll)

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


4. UML cho Quy Trình Tính Lương (Sequence Diagram)

Nhân viên (Employee): Gửi yêu cầu lấy thông tin ca làm việc và tính toán lương.

+ Hệ thống Bảng lương (Payroll System):
+ Gửi yêu cầu tới dịch vụ ShiftService để lấy thông tin ca làm việc.
+ Sau khi nhận thông tin ca làm việc, hệ thống tiếp tục tính toán lương và gửi yêu cầu tới PayrollService để tính toán bảng lương.
+ Sau khi nhận được thông tin lương từ PayrollService, hệ thống trả lại cho nhân viên kết quả bảng lương.

![PlantText](https://www.planttext.com/api/plantuml/png/Z991YW8n44NtEKNXtWku4455PpTCdw1eImnK9srIKN8s5nx9AzXj9v8MnTc5oiklnoUtotNX1Ps4XfN2Mgo3TTEoZKIgxUQwrYqQWSalHcUPeOfUg9a0-dGSOzL1xmKgSYTTqq3rapJu45dGQPPvbMLWEa_xO0P_T0paPOY67xEtha7HrgY4z72njdkoeOolI52pLoDWd2x1cIAyI7tgpBfxUowXBwh8w28iaUl0_tRTsk2-cpweLzDnaHsSLrDoKI_4kme6wMTZxsfOQTyonXog5cHs_MUw0m00__y30000)


5. In phiếu lương (Print Paychecks)

- Actor tham gia: Payroll Administrator.

Dòng chảy chính

1. Hệ thống tạo tệp phiếu lương.
2. Gửi lệnh in qua `IPrintService`.
   
 + Dòng chảy thay thế
 
- Nếu không tìm thấy máy in, thông báo lỗi và yêu cầu kiểm tra kết nối.
  
 + Biểu đồ tuần tự:
   
![diargam](https://www.planttext.com/api/plantuml/png/T90n2W8n44Nxd68ku0Ms4CN2Ta4BBMDssGJZH6CYU0AluI8Y20iMLjbYYu3to0cyWgiY1DHouCtxV-PUDxsreThOXIIK6QKXfLkjfEnd2u5afYncL6yXrGBDADSRmNB259gM-Q23zoXpJKYy3PtkDvB0r9yjiE1E5bfcoKLmZGLvkznABCZNmiiIfISm37KbG8PwX_od8gAXyxl4n9SCa0TNuLF1bTyZcE2Eva-3wAu4njnViO2PBnNCssm3AnlSeJMHNexPyvaF0000__y30000)

Lý do thiết kế:

- Việc in phiếu lương cung cấp bằng chứng rõ ràng về các khoản thanh toán cho nhân viên.
- Sử dụng giao diện `IPrintService` đảm bảo khả năng tương thích với nhiều loại máy in khác nhau.
- Quản lý lỗi kết nối máy in giúp người dùng nhanh chóng phát hiện và sửa chữa vấn đề.

##

# II. Giải thích tổng hợp các ca sử dụng

Lý do thiết kế hệ thống

- Tính toàn vẹn dữ liệu
  
    - Mỗi ca sử dụng đều bao gồm bước xác thực và kiểm tra tính hợp lệ, đảm bảo dữ liệu được xử lý chính xác.
    
- Đơn giản hóa quy trình
  
    - Thiết kế từng ca sử dụng tương ứng với các chức năng cụ thể trong tài liệu.
    
- Tăng khả năng tái sử dụng
  
    - Các phân hệ (Subsystem) như `BankSystem`, `PrintService` được thiết kế thành các giao diện độc lập, dễ dàng tái sử dụng trong các hệ thống khác.
    
- Đáp ứng yêu cầu người dùng
  
    - Căn cứ trên tài liệu, các ca sử dụng đã bao phủ toàn bộ quy trình hoạt động của hệ thống tính lương.
    - Mỗi ca sử dụng được thiết kế để giải quyết các yêu cầu của người dùng cuối (như nhân viên, quản lý nhân sự, kế toán) và đảm bảo hệ thống hoạt động như mong muốn.
    - Hệ thống được thiết kế sao cho có thể mở rộng khi cần thêm các ca sử dụng mới.

- Hỗ trợ các yêu cầu pháp lý và bảo mật

    - Hệ thống cần hỗ trợ các yêu cầu pháp lý về số giờ làm việc tối đa, phụ cấp và nghỉ phép.
    - Hệ thống Payroll phải bảo vệ thông tin cá nhân và tài chính của nhân viên bằng các biện pháp bảo mật như mã hóa dữ liệu, kiểm tra quyền truy cập, và sao lưu thường xuyên.

- Tối ưu hiệu suất hệ thống

    - Với các ca làm việc phức tạp (ca gãy, ca linh hoạt, làm thêm giờ), hệ thống cần có khả năng xử lý nhanh chóng và chính xác, tránh gây trì hoãn trong việc trả lương cho nhân viên.
    - Hệ thống cần hỗ trợ nhiều loại ca làm việc và tính năng mở rộng như tính lương cho ca làm việc linh hoạt hoặc theo dõi ngày nghỉ phép.

