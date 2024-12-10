# Thiết kế các lớp trong hệ thống Payroll System


I. BankSystem Subsystem

  Các lớp và phương thức:

  1. BankSystem

  + Phương thức:
      deposit(aPaycheck: Paycheck, intoBank: BankInformation)
  + Chức năng: Thực hiện giao dịch gửi lương vào tài khoản ngân hàng của nhân viên.

  2. BankTransaction

  Thuộc tính:
    + amount: float
    + transactionOperation: BankOperation
    + routingNumber: String
    
  Phương thức:
    create(op: BankOperation, amount: float, routingNum: String)
    
  Chức năng: Tạo giao dịch ngân hàng dựa trên thông tin phiếu lương.
  
  3. BankInformation

  Thuộc tính:
  
  + name: String
  + routingNumber: String
    
  Chức năng: Lưu thông tin tài khoản ngân hàng của nhân viên.
  
Quan hệ:

  + BankSystem sử dụng BankTransaction để thực hiện giao dịch.
  + BankTransaction được liên kết với BankInformation và Paycheck.


2. PrintService Subsystem
Các lớp và phương thức:

PrintService

Phương thức:
print(aPaycheck: Paycheck, onPrinter: String)
Chức năng: In phiếu lương dựa trên thông tin đã cung cấp.
PaycheckPrinterImage

Phương thức:
create(fromPaycheck: Paycheck)
buildPrintImage()
Chức năng: Tạo hình ảnh phiếu lương dựa trên thông tin từ phiếu lương.
PrinterInterface

Phương thức:
print(theImage)
Chức năng: Quản lý giao diện kết nối với máy in.
Quan hệ:

PrintService phụ thuộc vào PrinterInterface để giao tiếp với các máy in.
PaycheckPrinterImage được sử dụng để tạo hình ảnh phiếu lương.
3. ProjectManagementDatabase Subsystem
Các lớp và phương thức:

ProjectManagementDatabase

Phương thức:
getChargeNumbers(criteria: String): ChargeNumList
initialize()
Chức năng: Truy xuất và khởi tạo cơ sở dữ liệu quản lý dự án.
ChargeNumList

Phương thức:
new()
add(theChargeNum: ChargeNum)
Chức năng: Lưu trữ danh sách các mã dự án đã truy xuất.
ChargeNum

Thuộc tính:
projectName: String
value: String
Phương thức:
new(projectName: String, value: String)
Chức năng: Lưu thông tin chi tiết của từng mã dự án.
Quan hệ:

ProjectManagementDatabase sử dụng DBChargeNumbers để truy xuất mã dự án.
ChargeNumList chứa danh sách các đối tượng ChargeNum.
