# Hệ thống con trong hệ thống Payroll System

1. Payroll Processing Subsystem: 

  - Xử lý các công việc liên quan đến tính toán và phân phối lương.

  Chức năng:
  
  Đây là hệ thống con xử lý tính toán lương, quản lý phương thức thanh toán và phát hành phiếu lương.

  + PayrollController: Chịu trách nhiệm kiểm tra xem có phải ngày trả lương hay không, tính toán số tiền lương và xử lý thanh toán.
  + Employee: Lưu thông tin nhân viên, bao gồm phương thức thanh toán (chuyển khoản ngân hàng hoặc nhận phiếu lương trực tiếp).
  + Paycheck: Đại diện cho phiếu lương được tạo ra sau khi tính toán.

  Luồng hoạt động:

  + PayrollController kiểm tra thông tin ngày thanh toán và tính toán lương dựa trên dữ liệu Employee.
  + Tạo phiếu lương (Paycheck) và chuyển thông tin này đến ngân hàng hoặc dịch vụ in ấn.


![PhantText](https://www.planttext.com/api/plantuml/png/V54x3i8m3DrxYYWJ3Bq00q821WQaIfp0fAPKpQUAtQ52FHa3H-8Af2A2b4fuYUBtyOlpl3ysnE2vCpfhGJLGeP05zDvfBGhl51BLjXAdxamzCHefRfa8fJGGYSZSEilZYJwYxwefu2NqYsNILA1Lfu6n-04gvD0oQFc8V7Nb16pVKI8XGaEIP6zQxNh4IG0B1fChHiwXJ9tJcJFRC51TKJKJMp2kipprs8KN9UhvOl9y_Gsv4lAp1n8Nv-KVrIT3K5LeqOyYcGtP1cqvVjmB003__mC0)

2. Timecard Management Subsystem:
  - Quản lý thông tin thời gian làm việc của nhân viên.

  Chức năng:
  
  Quản lý thông tin thời gian làm việc của nhân viên, bao gồm ghi nhận giờ làm việc, cập nhật thông tin và lưu trữ dữ liệu.

  + TimecardController: Xử lý việc lấy, cập nhật, và lưu dữ liệu thẻ thời gian.
  + Timecard: Chứa thông tin về số giờ làm việc và kỳ lương

  Luồng hoạt động của Timecard Management Subsystem:

  + TimecardController truy vấn thẻ thời gian hiện tại của nhân viên từ hệ thống.
  + Nhân viên nhập hoặc chỉnh sửa số giờ làm việc của mình thông qua giao diện.
  + TimecardController lưu các thay đổi và cập nhật dữ liệu trong hệ thống.


  ![PhantText](https://www.planttext.com/api/plantuml/png/V54x2i904Ett5CjMMkG25Y842mj1KB0UiqCKznDcTeKWdip28ta5rqyqqU2KxxrvRpxNysN20IX4QqG5nHvAb6grirW0QJa7bm2BBiXbt73D0QsIHo5J5GQOPIFDlGlaZK5wqSygCUIHA1aqmi6mHSTAGy1UYk7mJPnwSZjfMn-9rvxsg5je1VK2QUVrZydKLiRNY1qJV86pjeS3YwtsdgspRFmPQYILVPoErJ_zEp_fDsYyAra6hyH9JD3f-qjk0000__y30000)
  
3. Security Subsystem:
  - Bảo mật truy cập và dữ liệu trong hệ thống.

  Chức năng:
  
  Đảm bảo bảo mật dữ liệu và giới hạn quyền truy cập chỉ cho những người dùng được ủy quyền.

  + SecurityManager: Xác thực thông tin người dùng (username và password) và kiểm tra quyền truy cập vào các chức năng của hệ thống.
  + User: Đại diện cho thông tin người dùng, bao gồm tên đăng nhập và mật khẩu.

  Luồng hoạt động:

  + Khi người dùng đăng nhập, SecurityManager xác nhận thông tin đăng nhập có hợp lệ không.
  + Nếu hợp lệ, hệ thống cấp quyền truy cập đến các chức năng tương ứng dựa trên vai trò của người dùng.


  ![PhantText](https://www.planttext.com/api/plantuml/png/N4-x3S8m4EqzXUKAYYn0WS80L1437FO9B6mdyfr10MKo2aPY1MmbI8PNlj-zUpzVBJ54Jjw90VG5JYXLXpf5owFiqf56OlHAFeJCq0w8v5VVGyZ-k6Wphk2i0SO3OLojAm4Id_jexxZJ6eaMRQfgI-IdAsKYWCUA6hBnraTJXV_NDCrshjf8LOvYOAlp8b9Y4Yq6Ktxz0000__y30000)
  
4. Bank System Integration Subsystem: 
  - Kết nối và giao tiếp với hệ thống ngân hàng bên ngoài.

  Chức năng:
  
  Tích hợp với hệ thống ngân hàng để thực hiện các giao dịch thanh toán lương.

  + BankSystem: Cung cấp các dịch vụ như chuyển khoản lương trực tiếp đến tài khoản nhân viên.
  + PayrollController: Gửi yêu cầu thanh toán lương đến hệ thống ngân hàng.
  
  Luồng hoạt động:

  + PayrollController tính toán số tiền lương cần thanh toán.
  + Gửi yêu cầu thanh toán qua API hoặc giao diện của BankSystem.
  + BankSystem thực hiện giao dịch và trả về trạng thái (thành công/thất bại).
    

  ![PhantText]
  
5. Printing Service Subsystem:
  - Hỗ trợ in ấn các tài liệu liên quan đến lương, như phiếu lương.

  Chức năng:
  
  Cung cấp khả năng in các tài liệu liên quan đến lương, ví dụ như phiếu lương hoặc báo cáo.

  + PrintService: Quản lý việc tạo ra các bản in cứng cho phiếu lương.
  + Paycheck: Là đầu vào chính để in phiếu lương.
  
  Luồng hoạt động:

  + PayrollController tạo ra phiếu lương (Paycheck).
  + Phiếu lương được gửi đến PrintService.
  + PrintService tạo ra bản in cứng và phân phối đến nhân viên.
  

  ![PhantText]
  
6. Database Management Subsystem:
  - Quản lý và lưu trữ dữ liệu trên cơ sở dữ liệu, bao gồm thông tin nhân viên, phiếu lương, và dữ liệu thời gian làm việc.

  Chức năng:
  
  Quản lý dữ liệu liên quan đến nhân viên, thời gian làm việc và phiếu lương trên cơ sở dữ liệu.

  + PayrollDBManager: Lớp quản lý giao tiếp với cơ sở dữ liệu, bao gồm các chức năng truy xuất và lưu trữ thông tin.
  + Employee, Timecard: Các đối tượng dữ liệu chính được lưu trong cơ sở dữ liệu.
  
  Luồng hoạt động:

  + PayrollDBManager thực hiện lưu trữ hoặc truy vấn thông tin nhân viên và thời gian làm việc.
  + Mọi giao dịch (transaction) đều được thực hiện trong ngữ cảnh an toàn để đảm bảo tính toàn vẹn dữ liệu.


  ![PhantText]
  
7. Login and User Authentication Subsystem:
  - Xử lý xác thực người dùng và tạo các phiên làm việc an toàn.

  Chức năng:
  
  Xử lý việc đăng nhập của người dùng và tạo phiên làm việc an toàn.

  + LoginController: Quản lý các yêu cầu đăng nhập và đăng xuất.
  + User: Lưu thông tin đăng nhập của người dùng (username, password).
  
  Luồng hoạt động:

  + Người dùng nhập tên đăng nhập và mật khẩu qua giao diện.
  + LoginController xác thực thông tin với sự hỗ trợ của SecurityManager.
  + Nếu thành công, tạo một phiên làm việc an toàn và cấp quyền truy cập cho người dùng.


  ![PhantText]
  
