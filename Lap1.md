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
