# Lab 3: Indentify context elements

  # 1. Sybsystem context diagrams
    
    Hệ thông con của BankSystem, PrintService, ProjectManagementDatabase subsystems.

Biểu đồ ngữ cảnh của hệ thống con BankSystem:
1. Nhận chỉ thị thanh toán (Payment Instructions):**
-Nhận yêu cầu thanh toán từ **Payroll System**, bao gồm các thông tin như:
    - Số tiền thanh toán.
    - Tài khoản ngân hàng của người nhận.
    - Các chi tiết giao dịch liên quan.
 2. **Xử lý thanh toán (Payment Processing):**
- Xác thực thông tin giao dịch.
- Thực hiện giao dịch qua ngân hàng.
 3. **Cung cấp số dư tài khoản (Account Balance):**
- Cung cấp thông tin số dư tài khoản cho các hệ thống liên quan để báo cáo và kiểm tra.
 4. **Gửi sao kê ngân hàng (Bank Statements):**
- Tạo sao kê chi tiết về các giao dịch đã xử lý.
- Gửi sao kê đến các hệ thống khác, như dịch vụ in ấn (PrintService).

![PlanText](https://www.planttext.com/api/plantuml/png/pLEnJiCm4Dqj-H-iCj0CKVSgYaeHGoI6YaoCnhYjXMD7lWiG0V-ExP8qRWipsvtzxkwzy_CAa3li6at9DRkr1ftreT0SWCqslFUfhdj0sSmO1vQSiA8GXugoP1-KCBPOC93cEU8QQP1L1j1r0fKrGCaN9M5CPL2wBHUI4ZM4h5fpyr9BzwfyKXGZPcZTEYiam4_ZEPzqPijXtkGm2qKxYJT2sCxWccjkX9nd7fmU1LmWNIFtccBlCVJWI6l8ir53tJt1OGaRPz_xSMKHVjpNCVMQOAnfGurNTdMlTdjyb5hRjtyfyywWmb7T-NYlIaP8MPw0l9UsoZNy5rHAxW8W8PJS1ruFKiVEi5UjDrPgopmlKpij_tHbwhpFF9-y6YMJ5mnzBwWxmvmk_kGwKKR9obEB_-yR "BankSystem")

 Phương thức 
- processPayment(aInstruction: PaymentInstruction): Xử lý các thanh toán chỉ định từ hệ thống khác.
  - Tham số: aInstruction(giao dịch thông tin cần thanh toán).
  - Trả về: Một đối tượng PaymentConfirmationđược nhận dạng giao dịch trạng thái.
- getAccountBalance(): Lấy số dư tài khoản hiện tại từ ngân hàng.
  - Trả về: Đối tượng AccountBalancechứa thông tin về số dư tài khoản.
- sendStatement(aStatement: BankStatement): Gửi sao kê ngân hàng.
  - Tham số: aStatement(thông tin sao kê ngân hàng).
  - Được gửi đến các dịch vụ khác, chẳng hạn như PrintService , để in hoặc lưu trữ.
Mô tả giao tiếp:
- Payroll System gửi thông tin giao dịch (qua PaymentInstruction) tới BankSystem qua phương thức processPayment(). BankSystem trả về PaymentConfirmation xác nhận kết quả.
- BankSystem gửi sao kê ngân hàng (qua BankStatement) tới PrintService để in ấn.
- BankSystem cung cấp số dư tài khoản (qua AccountBalance) qua phương thức getAccountBalance() cho các hệ thống tài chính khác.

# **PrintService**
#### PrintService là một hệ thống con trong Payroll System, chịu trách nhiệm xử lý các yêu cầu in ấn. Cụ thể, nó đảm nhận việc nhận tài liệu cần in (như phiếu lương Payslip) và tương tác với máy in để hoàn tất quá trình in.
### Biểu đồ ngữ cảnh của hệ thống con PrintService

     Biểu đồ ngữ cảnh của hệ thống con PrintService:
 ![PlanText](https://www.planttext.com/api/plantuml/png/Z9DDRi8m48NtEOML5KWD1uYgYWLTP8UK4mpEG2qSEx8d4QZbP5rm9AvGvyUDGr2fLoFFyyoNDvFRztLj2GpLfOmgu4Su88lpUcVFbh1aMwDFvvXzHimTBi5QToKKvMWQmN58zATg4nlDwn8LBOeXI9c_UkaLQDA-1ffboXejYg06_q1-x3iGK6qNmvEiI5bEBZuiVT2zkaINQEH-LoJe3jTtdw1wkB5ioA1TnnPybjbhKy8yaIH986f0YW88Vvrmn3kj9O8QaE_DH3FtCVpa86SxLnuafEP0GgidSCzc54vawctMCks1exTN-0kM_NCbOFDW9xJQ_h4L7SEaV9AyZJDDMLmPpT5QjF5SvzrrihfJJ4bVlrQhwJexeIWhYMrn9r-ZAjeVumS00F__0m00")

Phương thức
- getProjectInfo(projectId: String): ProjectData
  - Mô tả: Truy vấn thông tin dự án dựa trên mã dự án projectId.
  - Đầu vào: projectId (String)
  -Đầu ra: ProjectData (Thông tin chi tiết về dự án)
Mô tả giao tiếp
- PayrollController -> IProjectDatabase (Yêu cầu thông tin dự án)
- #### IProjectDatabase -> ProjectManagementDatabase (Truy vấn dữ liệu)
- #### ProjectManagementDatabase -> ProjectData (Trả về thông tin dự án)
  
      Biểu đồ ngữ cảnh của hệ thống con ProjectManagementDatabase subsystems    
![PlanText](https://www.planttext.com/api/plantuml/png/f5AzJiCm4Dxz5ASoq0vHzwgoAW5392fLT6Ay9jVKoB63VG4YuCaOU2HU0Rj98qiPkztvFdr_yj_FxyOpEcvhBMxXpXfsLej2e_Smss4NDZsyQd8pG0-JLrYlYtwH4Zu5m789hosvRkVi2nLyZuppXVWMGI4tJEw81GbrcI1FS0Vq5FX6sC1O4G-Wt1pjl1dc4bQmPwTCjGXJGjEBxTk3xpnJ7KyVtHYhnstHO4KrcL6uZxTDVFYHeOaCmStDewfE_4nQs_Shh3qOLdnnb5o39frFKaRO4sbaPOq_gSQBQVDP9gVrhSxjA_9GHiOtXM9QyLUM9L55aZfofdutPChuFVu1003__mC0 "ProjectManagementDatabase")



  # 2. Analysis class to design element map
    Ánh xạ các lớp phân tích đến các phần tử thiết kế
    
| **Analysis Class**             | **Design Element**              |
|--------------------------------|---------------------------------|
| **LoginForm**                  | **LoginForm**                   |
| **MaintainTimecardForm**       | **MainEmployeeForm**            |
|                                | **TimecardForm**                |
|                                |  **MainApplicationForm**        |
| **TimecardController**         | **TimecardController**          |
| **SystemClockInterface**       | **SystemClockInterface**        |
| **PayrollController**          | **PayrollController**           |
| **Paycheck**                   | **Paycheck**                    |
| **PaymentInstruction**         | **PaymentInstruction**          |
| **Employee**                   | **Employee**                    |
| **IEmployeeRepository**        | **IEmployeeRepository**         |
| **IPaymentRepository**         | **IPaymentRepository**          |
| **BankSystem**                 | **BankSystem**                  |
| **IBankSystem**                | **IBankSystem**                 |
| **ProjectManagementDatabase**  | **ProjectManagementDatabase**   |
| **IProjectDatabase**           | **IProjectDatabase**            |
| **ProjectData**                | **ProjectData**                 |

##

  # 3. Design element to owning package map
    Ánh xạ các phần tử thiết kế vào các gói

| **Design Element**         | **"Owning" Package**                       |
|--------------------------- |--------------------------------------------|
| **UserInterface**          | Middleware::Presentation::GUI Framework    |
| **PayrollController**      | Applications::Payroll::BusinessLogic       |
| **TimecardController**     | Applications::Payroll::BusinessLogic       |
| **EmployeeRepository**     | DataAccess::Employee::Repository           |
| **PaymentRepository**      | DataAccess::Payment::Repository            |
| **Database**               | DataAccess::Database::Connection           |
| **Paycheck**               | BusinessServices::Payroll::Artifacts       |
| **PaymentInstruction**     | BusinessServices::Payroll::Artifacts       |
| **IEmployeeRepository**    | Interfaces::Employee::RepositoryInterface  |
| **IPaymentRepository**     | Interfaces::Payment::RepositoryInterface   |
| **IBankSystem**            | Interfaces::Bank::SystemInterface          |
| **IProjectDatabase**       | Interfaces::Project::DatabaseInterface     |
| **BankSystem**             | Subsystems::Bank::PaymentProcessing        |
| **ProjectManagementDatabase** | Subsystems::Project::DatabaseManagement |
| **ProjectData**            | BusinessServices::Project::DataArtifacts   |

# 4. Architectural layers and their dependencies

![PlantText](https://www.planttext.com/api/plantuml/png/T5H1Rjim4Bph5Gltq5C-q4EHf6s00WaGnEq3LjJQOKroYLqgW13aPJtqIVr2ISgHOohLHSBCS7Q69FJtzvzBJIXfzAxJWmqH1Jru3cmUXJr1af7UC3sQmrvu38DXnm8VRkhJTH_XNaWf94oM0zpYHDB5hCOzmMRDRU2v0p3i8uVCmEQdaW1y3ubaXuOsW0gZFTVSyju6k67nbNQxS_eECtiLexDcdhGeFJRI7zQJGHbEahJhNagDwr5j85KemqnRv3rsLUKU9s7du0k7L3wA94-8vZyP6brgTDSO3h2TDD6SjDTcdF0lCWdkCEIClc1VCM6FEkzYz4C_ToimN1bJ2vmNMr6hLjzyT3mHmGD5LfjOfcgVNThsDKCZYwticFerQdFqDhw6tewzrl9wIdl2rfilDh-s94_sQ1LrDdeWLw-5FjeCZHOkBZxdGu5FC2ffvtODa2zDWwGPI0kGgGBqsW1bovT5hIQjDVdgBvEYy9CTYjTxODcNjyjFQct6z3EGhS-1k03Lea3Lz0XsbnI6_3lu1m00__y30000)
