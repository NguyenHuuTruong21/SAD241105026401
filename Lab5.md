# Hệ thống con trong hệ thống Payroll System

1. Payroll Processing Subsystem: 

  - Xử lý các công việc liên quan đến tính toán và phân phối lương.

  Chức năng:
  
  Đây là hệ thống con xử lý tính toán lương, quản lý phương thức thanh toán và phát hành phiếu lương.

  + PayrollController: Chịu trách nhiệm kiểm tra xem có phải ngày trả lương hay không, tính toán số tiền lương và xử lý thanh toán.
  + Employee: Lưu thông tin nhân viên, bao gồm phương thức thanh toán (chuyển khoản ngân hàng hoặc nhận phiếu lương trực tiếp).
  + Paycheck: Đại diện cho phiếu lương được tạo ra sau khi tính toán.
  + Timecard: Ghi nhận giờ làm việc của nhân viên.

  Luồng hoạt động:

  + PayrollController kiểm tra thông tin ngày thanh toán và tính toán lương dựa trên dữ liệu Employee.
  + Tạo phiếu lương (Paycheck) và chuyển thông tin này đến ngân hàng hoặc dịch vụ in ấn.


![PlanText](https://www.planttext.com/api/plantuml/png/T94zRiCm38LtdKAZC-W27ee0RO5sCv00dGcPTOn8Oa19Wr7qP1rwf5wX-h7Y54KcWT_JUoIbdw_llG_08LeZ1rYOZ1cOD7e_kqbe0zut_aWkv1DPVWWf9KUtAjqkrngCZWO29bh9X0wv0dr2VKxqKsoXXPKi1PQY2xryDmIXX34cO_U7txYVxSNGWbZTk5QlOozdb_tAWSLU7WBdDLBjmG0lDmqc38V2kbsZr_JZR543ZpNzH97z6_4PnyslBh0Co3CbzfGcNIDVjhjRRfM6PiX2iQH-_vzMgOVhTdVazdHtv3QzsACRqx-ANm000F__0m00)

2. Employee Management Subsystem:
  - Quản lý thông tin thời gian làm việc của nhân viên.

  Chức năng:
  
  Quản lý thông tin thời gian làm việc của nhân viên, bao gồm ghi nhận giờ làm việc, cập nhật thông tin và lưu trữ dữ liệu.

  + EmployeeController: Quản lý các thao tác liên quan đến nhân viên.
  + Employee Entity: Thực thể lưu trữ thông tin nhân viên.
  + SecurityManager: Kiểm soát quyền truy cập vào dữ liệu nhạy cảm.

  Luồng hoạt động của Employee Management Subsystem:

  + EmployeeController truy vấn thẻ thời gian hiện tại của nhân viên từ hệ thống.
  + Nhân viên nhập hoặc chỉnh sửa số giờ làm việc của mình thông qua giao diện.


  ![PlanText](https://www.planttext.com/api/plantuml/png/T9513e9034NtSufPme8Bi32eSU52DvoWGYN4qZ4pnOGOJ-R28ta5gGeQeil-zhzs_joljom8U6aRiglcIAv3t013XGsoc88WXB6nT2pU4Q6tPsEjhL26rfhtBiAXA5DRiyJfwDJfzbY2u4_3Pp0s5pFP-joLJDWgCJIzCnTVSwNr3lYWs6yj087lKhid1pAzkOpY0QRwjkUfChfLp9y0bL-8yRmSYzRNqhtIUYTo0ghrbVEYm12YDg0VU3rXuHmXi39-H9eaiqzUV_gJfIP3BlklCmy0003__mC0)


3. Timecard Management Subsystem:
  - Bảo mật truy cập và dữ liệu trong hệ thống.

  Chức năng:
  + Quản lý thẻ chấm công của nhân viên.
  + Xác nhận và tính toán giờ làm việc.
  
- **Mối quan hệ**: Tương tác với **Payroll Processing Subsystem** để cung cấp dữ liệu đầu vào.

  ![PlanText](https://www.planttext.com/api/plantuml/png/T57DQiCm3BxxANnCe7c174QXFMo7GQ23dTLOox8vLf2LGnbziXtsI7s5sbrgZsQz2A7lHtpIwVjdxGLOfi7gbtx05jWyWuCE1tIYMWlU9s13JfYiHTPVIclTeLoX0eVHqW7noTIwTxBI1WHhlGsrh9D3L4rZX99GvYQJoiXg6V-o5lRlDB5_9Vx4C7cp164smg51xiaiznxLJPPBWchf4gStFdFKnymjoioEK7CLHE0YIViQfWzi9TyqmB07Z-c4CsD31elnjvzJ1hETSE-wQFVF4whg8IUyWz_ThzReJ7YxEWC00F__0m00)

4. Bank System Integration Subsystem: 
  - Kết nối và giao tiếp với hệ thống ngân hàng bên ngoài.

  Chức năng:
  
  + Thực hiện các giao dịch ngân hàng để thanh toán tiền lương.
  + Xử lý các phương thức thanh toán (chuyển khoản, séc, ...).
  
  Luồng hoạt động:

  + PayrollController tính toán số tiền lương cần thanh toán.
  + Gửi yêu cầu thanh toán qua API hoặc giao diện của BankSystem.
  + BankSystem thực hiện giao dịch và trả về trạng thái (thành công/thất bại).
    

  ![PlanText](https://www.planttext.com/api/plantuml/png/T91D3e9038NtSuekCO4Bi32eSU6EX1FKeIXX_Z9J5XFZoLnu9AyWCfWG4tSlxUlNrxuUpoemUXwrWZsQeOc1IGkfC8IvSB26lLMAFDm403Xl9OLGOzHaE2Fjb8r49HmNbOF3AAyaXnBgHMt4NQoOQKdYjUHiw3b3RKV39NJA8kTmdcmxALEjOT-Rompf3PFlK1AS_f5ctq_qejYkprkDVZhVcA8YqqwV46y0003__mC0)


  
5. Printing Service Subsystem:
  - Hỗ trợ in ấn các tài liệu liên quan đến lương, như phiếu lương.

  Chức năng:
  
  Cung cấp khả năng in các tài liệu liên quan đến lương, ví dụ như phiếu lương hoặc báo cáo.

  + PrintService: Quản lý việc tạo ra các bản in cứng cho phiếu lương.
  + Paycheck: Là đầu vào chính để in phiếu lương.
  
  Luồng hoạt động:

  + PaycheckPrinter tạo ra phiếu lương (Paycheck).
  + Phiếu lương được gửi đến PrintService.
  + PrintService tạo ra bản in cứng và phân phối đến nhân viên.
  
  ![PlanText](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbkZa90KMPUIN1gKLbcSYfNSavYSJ6Aa48rbuA2GW58922nCZaZDJbRem3Ai5A02MborNB1D4E5m8Qa5a7qfwVcfHObbgJ295rIIn8pSufncOJY05rTExWiRXceTLmEgNafG6zn0G000F__0m00)

  
6. Database Management Subsystem:
  - Quản lý và lưu trữ dữ liệu trên cơ sở dữ liệu, bao gồm thông tin nhân viên, phiếu lương, và dữ liệu thời gian làm việc.

  Chức năng:
  
  Quản lý dữ liệu liên quan đến nhân viên, thời gian làm việc và phiếu lương trên cơ sở dữ liệu.

  + PayrollDBManager: Lớp quản lý giao tiếp với cơ sở dữ liệu, bao gồm các chức năng truy xuất và lưu trữ thông tin.
  + Employee, Timecard: Các đối tượng dữ liệu chính được lưu trong cơ sở dữ liệu.
  
  Luồng hoạt động:

  + PayrollDBManager thực hiện lưu trữ hoặc truy vấn thông tin nhân viên và thời gian làm việc.
  + Mọi giao dịch (transaction) đều được thực hiện trong ngữ cảnh an toàn để đảm bảo tính toàn vẹn dữ liệu.


![PlanText](https://www.planttext.com/api/plantuml/png/R55B2i8m4Dtd5BEqYruW2n7HfIZK2qpJeNxIZybKAEB9N7Wahs3Q9XLfDu7toSnxoUVrNbb6mqsXOOECALfAcjIsbgaGIgEr8myF0G0MxzGnYymT4lRfXHH7dP8JzyAj8TDAIDYSopmA5l4KVju1MrDflLdliCISp6_kjgXrrT8mdpoG4EWe-8xdWXIQhFUn1n82FVhS9dKYTUrzjGSI0XtzCWqP4wwCgr_NbM6VgcDcwhgBuxF4yNBIIKnATgvGP5uDyUVL4Ff_xpItM56PkUyKNm000F__0m00)

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


  ![PhantText](https://www.planttext.com/api/plantuml/png/N8yn3i8m34NtdCBA14Clm82AMDaG1p2jLIfIfueTLGZrP0mSYIkGjaW4_lZi_x_zUZnBKGmQEsTwhAxO4DY3Rre6v1fEGW5sKI_4sbQehMSunhFSHAcpS3UGL3aKWTcqzwp1EvTSosoHcsQhzI_nKJzep6BcnjmR4s3iA4DzMXnyg3FpVtjHR9Ue3LZytazYpMXAudfw-0q00F__0m00)
  
