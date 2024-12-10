# Thiết kế các lớp trong hệ thống Payroll System


# I. BankSystem Subsystem

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


![PlantText](https://www.planttext.com/api/plantuml/png/Z99BReCm48RtdC9Y1H9SW4MKLkgYcwOIlS34cL04ViWUBr2KatNH8_KAvI7849IgNetjR_wPV-oVh--z9t0KL1jPa0rKAE9dq4tPUK8bod3qOnIBIoJw9LlmNZ1YEfxM2QtnDINm3ftyHDaKOeuoKMioGrunPh_git4Ag3Ow7HMkqPt-XmFjGGu4Av8BK2PeAiIvDK3id6xymQ8RfQTQovRHpWIgTVKMr15T8Kfo_OvPaGw1C37sJY9Rry-OqApom0zplFAZGU6cWRyQN2dFy_t7Y1PJVHzFd4XlpyJW2ccYadIhr5--ADkQ3d6udcFU7_iZURxRF6aXuk3HnuzOFguDouM6X6KAFMcTaUX7_1hjKP-6l_qB003__mC0)


# II. PrintService Subsystem

  Các lớp và phương thức:

  1. PrintService

  + Phương thức:
    
    + print(aPaycheck: Paycheck, onPrinter: String)
      
  + Chức năng: In phiếu lương dựa trên thông tin đã cung cấp.

  2. PaycheckPrinterImage

  + Phương thức:
    
    + create(fromPaycheck: Paycheck)
    + buildPrintImage()
      
  + Chức năng: Tạo hình ảnh phiếu lương dựa trên thông tin từ phiếu lương.

  3. PrinterInterface

  + Phương thức:

    + print(theImage)
    + Chức năng: Quản lý giao diện kết nối với máy in.

  Quan hệ:

  + PrintService phụ thuộc vào PrinterInterface để giao tiếp với các máy in.
  + PaycheckPrinterImage được sử dụng để tạo hình ảnh phiếu lương.


![PlantText](https://www.planttext.com/api/plantuml/png/T55B3e8m4Dtt59EkCD4Bi31itP5mWbe6QQH0Egs664xcmYDv1Md51BJEefbatc-cp_iZ8okCTRfXlP1dSKBWkL6jBT1Sb4Get946igWvt1XC9Hj112lCU_2ktWyIaOj1rYZFANowBNHjOA59eR1JTze4tiYMkZDwHXwqJxJKbmQ5nQGodVxrs2o0HwUQCiW4aIHcDflufnBHHMoDWPv6awqqLoVPxVRnNLBWZf3u7yfteWakEwrTg-IqDi5LsNhcnjINje4RhaNWpyNPo39iI__NBm000F__0m00)


# III. ProjectManagementDatabase Subsystem

  Các lớp và phương thức:

  1. ProjectManagementDatabase

  + Phương thức:
    
    + getChargeNumbers(criteria: String): ChargeNumList
    + initialize()

  + Chức năng: Truy xuất và khởi tạo cơ sở dữ liệu quản lý dự án.

  2. ChargeNumList

  + Phương thức:

    + new()
    + add(theChargeNum: ChargeNum)

  + Chức năng: Lưu trữ danh sách các mã dự án đã truy xuất.
  
  3. ChargeNum

  + Thuộc tính:

    + projectName: String
    + value: String

  + Phương thức:
    + new(projectName: String, value: String)
    + Chức năng: Lưu thông tin chi tiết của từng mã dự án.

  + Quan hệ:

    + ProjectManagementDatabase sử dụng DBChargeNumbers để truy xuất mã dự án.
    + ChargeNumList chứa danh sách các đối tượng ChargeNum.


![PlantText](https://www.planttext.com/api/plantuml/png/h9B1Ri8m38RlVGghfoAjBz33X0R73KtY2TpKAjcQW69d4qmysGuy4g-mbW1A1jrfliN-F_kFa-FtOSg2JhpfiWsgTsm9ybUtVYCbBsZxeo4hSnIiaGcMlkOj2vaSlZBeGtN83ED0K8LeIMOhT2qjlAd9SQ6S5d8QArYAqxQTL70LF6kMYDLMYyPExwYOdDBxB9gVKCbCIvzd80GsJI4hkWBHnB_wHZrBs8JRBj3GnNbK_S3Et-Q3aplaGmhSCJ5_IhOskj9_sUVuIvRbuusL2dBFnFa9_LqSWFHXUhaZySwUYRIQw0UjMbj1FOZtsPHiC_pH7m000F__0m00)


# 4. Payroll Subsystem

  Các lớp và phương thức:

  1. PayrollController

  + Phương thức:

    + calculatePay()
    + processPayment()

  + Chức năng: Tính toán và xử lý thanh toán lương cho nhân viên.

  2. Employee

  + Thuộc tính:
    + name: String
    + employeeId: int

  + Phương thức:
  
    + getEmployeeID(): int

  + Chức năng: Lưu thông tin nhân viên.

  3. Paycheck

  + Thuộc tính:

    + amount: float
    + payDate: Date

  + Phương thức:

    + create(forAmount: float): Paycheck
    + Chức năng: Lưu trữ thông tin phiếu lương.

  + Quan hệ:

PayrollController tạo và quản lý Paycheck dựa trên thông tin từ Employee.


![PlantText](https://www.planttext.com/api/plantuml/png/V54xRiCm3Drr2aAJC_W26e8KJOTi1N82Lg7T8FeO55t027Ao33rIhr0QTHe51Sf10juZt-EJlgwVcoB8CiPW1lGdx0diAqwSGu3z-5Qc8XGjd0re-O2bm48_voJpJRomF-Kn-36WaBOrgueOE7igHU58IHRgOYhXbpY4F15LUYqaZEHWBtnCVGNJqhixE3WcgNnwaflGRjkixlI3bwxXtycV7hmmvZ69Wovab0eVSDfg8WVpMMTbKg3fCZ_La-fvaw-D_xvRswxleHrO9er97rHqvov3npdQVqP_C-XeJubObodMNCo6qc7-qMy0003__mC0)


## Trạng thái và thay đổi trạng thái

  Một số trạng thái chính trong hệ thống:

  + Timecard:

    + Trạng thái: New, Updated, Saved.
    + Thay đổi trạng thái: Khi nhân viên nhập giờ làm, trạng thái từ New chuyển sang Updated. Sau khi lưu, chuyển sang Saved.


![PlantText](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XUGKPAgeEINMgwaa5Yi0AHXGg45AK0w1ImCPSEaWXFBe19W5XTNj5QiWgwk7LWx48FPK3qALWfA7lcbHSKAhdabgKL0VLmm6P0gi04WDI26Gac-WekJ4XT442GDD9ZB8JKl1UHK00000F__0m00)


  + Paycheck:

    + Trạng thái: Pending, Processed, Deposited.

    + Thay đổi trạng thái:
    
      1. Khi phiếu lương được tạo, trạng thái là Pending.
      2. Sau khi tính toán, chuyển sang Processed.
      3. Sau khi gửi đến ngân hàng, chuyển sang Deposited.


![PlantText](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XUGKPAge1IGcfUIcPUkf91Oh01bmwMAyfDJYujJKo2IC1vCsYMr8ByuimGg3UTnSKLhnIhewjh1ZOFI436OAGfMG0iIAuloSt8Kd1Dpaajp4a56SI4KW9J3JGKf3qxDAr4eoLTmIipBLk92I84K0ktaSW3Q0_8P0000__y30000)
