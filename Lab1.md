
# 1. Phân tích kiến trúc
Đề xuất kiến trúc
Kiến trúc hệ thống:

# Kiến trúc ba lớp (Three-Tier Architecture):
+ Presentation Layer: Giao diện người dùng, nơi người dùng tương tác với hệ thống.
+ Business Logic Layer: Xử lý các quy tắc nghiệp vụ và logic của hệ thống.
+ Data Access Layer: Truy cập và quản lý dữ liệu từ cơ sở dữ liệu.
# Giải thích lý do lựa chọn
+ Tính phân tách: Kiến trúc ba lớp giúp phân tách rõ ràng giữa giao diện người dùng, logic nghiệp vụ và dữ liệu, từ đó dễ dàng bảo trì và mở rộng.
+ Khả năng mở rộng: Mỗi lớp có thể được mở rộng độc lập mà không ảnh hưởng đến các lớp khác.
+ Bảo mật: Thông qua việc phân tách, có thể áp dụng các biện pháp bảo mật hiệu quả hơn cho từng lớp.
# Ý nghĩa từng thành phần trong kiến trúc
+ Presentation Layer: Cung cấp giao diện người dùng, cho phép người dùng nhập dữ liệu và nhận thông tin.
+ Business Logic Layer: Chứa các quy tắc nghiệp vụ như tính toán lương, quản lý thời gian làm việc.
+ Data Access Layer: Quản lý kết nối và tương tác với cơ sở dữ liệu, thực hiện các truy vấn SQL.
  
# Biểu đồ package mô tả kiến trúc

![Phantnet](https://www.planttext.com/api/plantuml/png/b5BB2i8m4BptAnRl_eBukWWLApukqiEQhYNORcIJ7aJyCWz-ahzWJ0LHW-0UPsPdCc5lbslVEXJNr5LoGBN7ag2J2LbYXquRXXIF91qu9U1dix8a01Ds93jKb4CBJ_ZGE5XZfOkmbIVdvEKtRAnciXPIKshruPZXKKnLGIP6UOtcCc-9fQv9eHGmHVOsjN_Havdzo1gZGnWe5UBUWXxC5Yt1o32JQbS3ivYdC6z8DDbWzjsosujr_8Q2CDOe1WPnj6KK_TyxsZYA1ldRD_I92tyKTm000F__0m00)


# 2. Cơ chế phân tích
Đề xuất các cơ chế cần giải quyết
+ Quản lý giao dịch thanh toán: Cần có cơ chế để xử lý và ghi nhận các giao dịch thanh toán, đảm bảo tính chính xác và kịp thời.
+ Quản lý thời gian làm việc: Cần có cơ chế để ghi nhận thời gian làm việc của nhân viên, bao gồm việc vào ra, nghỉ phép, và các trường hợp đặc biệt khác.
+ Báo cáo tài chính: Cần có cơ chế để tạo báo cáo tài chính, giúp người quản lý theo dõi chi phí và thu nhập.
+ Bảo mật và phân quyền: Cần có cơ chế bảo mật để đảm bảo rằng chỉ những người có quyền hạn mới có thể truy cập và thực hiện các thao tác nhất định trong hệ thống.

# 3. Phân tích ca sử dụng "Select Payment"
Lớp phân tích cho ca sử dụng "Select Payment"
+ PaymentController: Quản lý các yêu cầu thanh toán từ người dùng.
+ PaymentService: Chứa logic nghiệp vụ để xử lý thanh toán.
+ PaymentRepository: Truy cập dữ liệu để lấy thông tin thanh toán từ cơ sở dữ liệu.

# Biểu đồ sequence

![Phantnet](https://www.planttext.com/api/plantuml/png/T9513i8W44Ntd6AMkl02B4mJFO3HU809Z4f2WS1eqhEvy4XUGPhIqAIuvV_t_ypmVN-wn1ZvsLk1Yds4Qw8eGduooWHq32SSUd9yy8wZjxQjNYY-ZAAMTARWaydHWn1ZEC1klmwLaCYIuY9ijc9bMN2bJiATPk98ZCQc2XRFWggJIBWHgyUC8cFbggjL68cVqO7EoF-YvLe529C2UXgplTru7WdQf61nM24TEPt_wGS00F__0m00)

# Nhiệm vụ của từng lớp phân tích:
+ PaymentManager: Xử lý yêu cầu thanh toán và tương tác với cơ sở dữ liệu.
+ Employee: Đại diện cho người dùng yêu cầu thanh toán.
+ PayrollDBManager: Cung cấp dữ liệu thanh toán từ cơ sở dữ liệu.
  
# Biểu đồ lớp mô tả lớp phân tích:

![Phantnet](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niK90OcLkQbw9Rs9UOdfgaK8rbm8O5AKMbgOMbq1bDJIXmYcPnGKvYPK8uLekg3ckkGKv-PMfgN0JqbDBN59B4ZDpYf6L0NKMvUVak3YXMmXK3ZKLHHUQytHrxH0sMIcK5gSMOrE2OGjKgKDgNWhGwm00003__mC0)

# 4. Phân tích ca sử dụng Maintain Timecard
Xác định các lớp phân tích:

+ TimecardManager: Quản lý các hoạt động liên quan đến thời gian làm việc.
+ Employee: Đại diện cho nhân viên trong hệ thống.
+ TimecardDBManager: Quản lý truy cập đến cơ sở dữ liệu liên quan đến thời gian làm việc.

# Biểu đồ sequence:

![Phantnet](https://www.planttext.com/api/plantuml/png/UhzxlsjkGKv-PMggWgwTGaXcRcfoOb6ARs9UOdfgaPL2KMfXQMfn2Kmyj20biIHLGvCBJI6oNXSdkEvIi7AO198sk1fibW80003__mC0)

# Nhiệm vụ của từng lớp:

+ TimecardManager: Quản lý việc cập nhật và truy xuất thông tin thời gian công.
+ Timecard: Lưu trữ và xử lý thông tin thời gian công.
+ Employee: Cung cấp thông tin cần thiết cho việc cập nhật thời gian công.

# Biểu đồ lớp mô tả lớp phân tích:

![Phantnet](https://www.planttext.com/api/plantuml/png/Z9BDIiGm58NtVOgx745Ve8ZCOWG5HmGLrzVcqWdcf-P76CGdS-4Z-GecdIJziGFJHIddddFvSfhVxv-rTMYSbwAg6e7MmhNiXDuJmMS5uRa0IiBjfeP7PxXgqq2Xf9dakAG63RlZrjKGtvTFIRhgBG0jkIojpevuaB7Y2NloTx1_QCwghuJwe0Llw3ydB83EjJ4fd89wp3HXXH4i5DfSRHvjKM5BfZHyGck6tZtPWlFSCNIq2lNdttKE2qKTiepRJk3-a1bWH-6Xs1bfGOpHMOCxxOrzqUQDM0rSkIGtEpGjtNlvIcQI0F0zGG7e5_JHAM-eVKCEkR3nWamsn54y-89-C-34SGGAnrcJOk5o_m400F__0m00)

# 5. Hợp nhất kết quả phân tích
Sau khi phân tích hai ca sử dụng "Select Payment" và "Maintain Timecard", chúng ta có thể hợp nhất kết quả để tạo ra một cái nhìn tổng thể về hệ thống "Payroll System".

# Kết quả hợp nhất:

+ Kiến trúc tổng thể: Hệ thống bao gồm ba lớp chính: Client Layer, Business Services Layer, và Database Layer. Mỗi lớp có nhiệm vụ riêng và tương tác với nhau để cung cấp chức năng cho người dùng.

+ Cơ chế chính: Các cơ chế như quản lý nhân viên, quản lý thời gian công, tính toán lương và xử lý thanh toán là rất quan trọng để đảm bảo hệ thống hoạt động hiệu quả.

# Ca sử dụng:

+ Select Payment: Xác định cách thức thanh toán cho nhân viên, với các lớp như PaymentManager, Employee, và Payment đảm nhận các chức năng khác nhau.
+ Maintain Timecard: Xác định cách thức cập nhật và quản lý thời gian công của nhân viên, với các lớp như TimecardManager, Employee, và Timecard.
