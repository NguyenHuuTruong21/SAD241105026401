1. Phân tích kiến trúc
Đề xuất kiến trúc
Kiến trúc hệ thống:

Kiến trúc ba lớp (Three-Tier Architecture):
Presentation Layer: Giao diện người dùng, nơi người dùng tương tác với hệ thống.
Business Logic Layer: Xử lý các quy tắc nghiệp vụ và logic của hệ thống.
Data Access Layer: Truy cập và quản lý dữ liệu từ cơ sở dữ liệu.
Giải thích lý do lựa chọn
Tính phân tách: Kiến trúc ba lớp giúp phân tách rõ ràng giữa giao diện người dùng, logic nghiệp vụ và dữ liệu, từ đó dễ dàng bảo trì và mở rộng.
Khả năng mở rộng: Mỗi lớp có thể được mở rộng độc lập mà không ảnh hưởng đến các lớp khác.
Bảo mật: Thông qua việc phân tách, có thể áp dụng các biện pháp bảo mật hiệu quả hơn cho từng lớp.
Ý nghĩa từng thành phần trong kiến trúc
Presentation Layer: Cung cấp giao diện người dùng, cho phép người dùng nhập dữ liệu và nhận thông tin.
Business Logic Layer: Chứa các quy tắc nghiệp vụ như tính toán lương, quản lý thời gian làm việc.
Data Access Layer: Quản lý kết nối và tương tác với cơ sở dữ liệu, thực hiện các truy vấn SQL.
Biểu đồ package mô tả kiến trúc
