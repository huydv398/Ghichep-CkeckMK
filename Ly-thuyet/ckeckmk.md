# Lý thuyết về CheckMK
## OMD - Open Monitoring Distribution
* **Phân phối giám sát mở** là một gói đóng kín bao gồm [Nagios](Note/Nagios.md) cùng với các tiện ích bổ sung cho việc thu thập, giám sát và vẽ dữ liệu đồ thị.
* Nó đi kèm với [Check_MK multisite](Note/Multisite.md), một cung cụ toàn diện giải quyết nhiều thiếu sót của Nagios. Nó cung cung cấp một giao diện web để dẽ dàng quản trị và cấu hình, một bảng điều khiển thân thiệt với người dùng, một hệ thống mạnh mẽ và các agent giám sát dễ cài đặt cho nhiều bản phân phối Linux.
* Nếu không có CheckMK multisite, chúng ta sẽ phải sử dụng các view khác nhau cho nhiệm vụ khác nhau và sẽ không thể cấu hình tất cả các thiết lập mà không cần phải làm việc với các tệp cấu hình.

OMD với Check_MK giúp mọi người dễ dàng thiết lập hệ thống theo dõi riêng của họ.

OMD là sự kết hợp của các phương pháp hay nhất về cách Nagios được thiết lập và tích hợp. Nó đã kết hợp tất cả các Plugin Nagios thế hệ 3 phổ biến nhất vào trong một gói đơn giản và dễ duy trì, dễ cài đặt và dễ nâng cấp. Một khi bạn đã chạy máy chủ Linux , cài đặt và chạy bộ giám sát OMD chỉ mất 10 phút với một lệnh. Quản trị viên thực sự có thể tiết kiệm thời gian, không cần phải biên dịch như Nagios. Hoặc mất thời gian tích hợp với Plugin vào cấu hình Nagios.

OMD là một profect được phát triển từ năm 2010. OMD sử dụng nhân kernel là Nagios Core, Kết hợp với các phần mềm mã nguồn mở khác để đóng gói thành một sản phẩm phục vụ cho nhu cầu giám sát, cảnh báo và hiện thị

