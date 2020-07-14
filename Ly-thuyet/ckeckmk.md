# Lý thuyết về CheckMK
## OMD - Open Monitoring Distribution
* **Phân phối giám sát mở** là một gói đóng kín bao gồm [Nagios](Note/Nagios.md) cùng với các tiện ích bổ sung cho việc thu thập, giám sát và vẽ dữ liệu đồ thị.
* Nó đi kèm với [Check_MK multisite](Note/Multisite.md), một cung cụ toàn diện giải quyết nhiều thiếu sót của Nagios. Nó cung cung cấp một giao diện web để dẽ dàng quản trị và cấu hình, một bảng điều khiển thân thiện và dễ sử dụng với người dùng, một hệ thống mạnh mẽ và các agent giám sát dễ cài đặt cho nhiều bản phân phối Linux.
* Nếu không có CheckMK multisite, chúng ta sẽ phải sử dụng các view khác nhau cho nhiệm vụ khác nhau và sẽ không thể cấu hình tất cả các thiết lập mà không cần phải làm việc với các tệp cấu hình.

OMD với Check_MK giúp mọi người dễ dàng thiết lập hệ thống theo dõi riêng của họ.

OMD là sự kết hợp của các phương pháp hay nhất về cách [Nagios](Note/Nagios.md) được thiết lập và tích hợp. Nó đã kết hợp tất cả các Plugin Nagios thế hệ 3 phổ biến nhất vào trong một gói đơn giản và dễ duy trì, dễ cài đặt và dễ nâng cấp. Một khi bạn đã chạy máy chủ Linux , cài đặt và chạy bộ giám sát OMD chỉ mất 10 phút với một lệnh. Quản trị viên thực sự có thể tiết kiệm thời gian, không cần phải biên dịch như Nagios. Hoặc mất thời gian tích hợp với Plugin vào cấu hình Nagios.

OMD là một profect được phát triển từ năm 2010. OMD sử dụng nhân kernel là Nagios Core, Kết hợp với các phần mềm mã nguồn mở khác để đóng gói thành một sản phẩm phục vụ cho nhu cầu giám sát, cảnh báo và hiển thị.

### Các bản phân phối

Năm 2015, phiên bản đơn giản của OMD ra đời gọi là Check_MK, Check_MK có 2 phiên bản là Check_MK Raw Edition (CRE) và Check_MK Enterprise Edition (CEE).

* **OMD-LABS** chứa tất cả các thành phần nguyên bản của OMD và một số Addons thêm vào như Grafana, InfluxDB, Neamon, Icinga 2.

* **Check_MK Raw Edition** tập chung vào Check_MK, đây là một gói nhỏ hơn chứa các thành phần để chạy Check_MK.

### OMD-LABS và Check_MK Raw

#### OMD-LABS 
* **OMD LABS-Edition** là một nền tảng giám sát và một khái niệm mới về cài đặt, duy trì và cập nhật một hệ thống giám sát được xây dựng trên Nagios. Không được tích hợp sẵn trong các bản phân phối Linux mà tích hợp vào hệ thống dưới dạng các Package rpm và deb.

Phiên bản stable là 2.40, thường thì 6 tháng sẽ có một phiên bản stable được phát hành.

OMD-LABS chứa nhiều thành phần phần mềm mới so với gói OMD thường (Check_MK). Một số cài đặt mặc định khác sẽ thay đổi.

Một số điểm khác của OMD-LABS với OMD thường (Check_MK)

Các thành phần phần mềm bổ sung: OMD-LABS Chỉ bổ sung các phần mềm mới và không loại bỏ bất kỳ phần mềm nào, làm cho OMD-LABS trở nên hoàn hỏa hơn, và có thể chuyển xang phiên bản khác bằng OMD Update.

* Lõi giám sát mới bên cạch Nagios 3, OMD-LABS còn chứa hai Cóe mới là Neamon và Icinga2. Trong khi Neamon hoàn toàn tương thích với định dạng Nagios 3 config thì Icinga2 sử dụng định dạng cấu hình mới.

* Biểu đồ Grafana/InfluxDB: Bên cạnh PHP4 Nagios OMD có đồ thị Grafana dựa trên InfluxDB. Để tạo mẫu đồ thị dựa trên mẫu, đã có Histou (Histou được thiết kế để thêm các mẫu vào Grafana từ dữ liệu của Nagios). Giao diện giữa core giám sát và InfluxDB được thực hiện trong thành phần Nagflux.
* Hệ thống con Prometheus: Bên cạnh việc giám sát truyền thống, OMD-LABS đi kèm với Prometheus bao gồm quản lý cảnh báo, PushGateway và BlackBox Exporter.
* LiveStatus Multitool Deamon

#### Check_MK Raw
Check_MK là một phần của OMD, hiện tại đang có 2 phiên bản Check_MK là [Check_MK Raw Edition (CRE)]() và [Check_MK Enterprise Edition (CEE)]()
## Check_MK
### Tổng quan Check_MK
* Check_MK được phát triển bởi Mathias Kettner, phát hành lần đầu năm 2018. Check_MK là sự kết hợp của Nagios, Check_MK, NagVis, PNP4Nagios, DocuWiki,... tạo nên sự linh hoạt trong giám sát
* Check_MK là một hệ thống giám sát CNTT. Khi bắt đầu nó là một phần mở rộng cho hệ thống giám sát **Nagios** cho phép tạo cấu hình dựa trên quy tắc bằng cách sử dụng Python và giảm tải công việc từ lõi **Nagios** để làm cho nó mở rộng hơn, cho phép nhiều hệ thống được giám sát từ máy chủ **Nagios**.

Nó đi kèm với một bộ kiểm tra hệ thống, một [mod_python]() và JavaScript dựa trên giao diện người dùng Web, và một Module cho phép truy cập nhanh vào lõi Nagios.

* Check_MK là một mã nguồn mở, đa nền và ứng dụng web dựa trên phân phối miễn phí được thiết kế từ những bù đắp để cung cấp cho người dùng với một cách mới để thu thập dữ liệu từ các hệ điều hành hoặc các thành phần mạng. Phần mềm [obsolete]() các [NRPE](), [check_by_ssh](), [NSClient]() và ứng dụng [check_snmp](). Nó cung cấp giảm đáng kể việc sử dụng CPU trên Nagios chủ, cũng như các thành phần tồn đọng được kiểm tra trên máy chủ.
* Ứng dụng bao gồm ba công cụ tuyệt vời, nhiều trang, một trạng thái tính năng giao diện để (GUI-Graphical User Interface) cho Nagios, dựa trên [LiveStatus]()