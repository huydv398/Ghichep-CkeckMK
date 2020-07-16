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

* Check_MK là một mã nguồn mở, đa nền và ứng dụng web dựa trên phân phối miễn phí được thiết kế từ những bù đắp để cung cấp cho người dùng với một cách mới để thu thập dữ liệu từ các hệ điều hành hoặc các thành phần mạng. Phần mềm [obsolete]() các [NRPE](), [check_by_ssh](), [NSClient]() và ứng dụng [check_snmp](https://vi.wikipedia.org/wiki/SNMP#:~:text=SNMP%20vi%E1%BA%BFt%20t%E1%BA%AFt%20t%E1%BB%AB%20ti%E1%BA%BFng,thi%E1%BA%BFt%20b%E1%BB%8B%20m%E1%BA%A1ng%20t%E1%BB%AB%20xa.)(*Tập hợp các giao thức kiểm tra các thiết bị mạng như Router, switch hay server và hỗ trợ vận hành các thiết bị này một cách tối ưu*). Nó cung cấp giảm đáng kể việc sử dụng CPU trên Nagios chủ, cũng như các thành phần tồn đọng được kiểm tra trên máy chủ.
* Ứng dụng bao gồm ba công cụ tuyệt vời, nhiều trang, một trạng thái tính năng giao diện để (GUI-Graphical User Interface) cho Nagios, dựa trên [LiveStatus](Note/livestatus.md); MK LiveStatus, một modules liên kết sự kiện; và **Wato**(*là tập hợp nhiều modules được sử dụng để cấu hình cho Check_MK server*), một giao diện cấu hình (GUI). Features tại một tính năng GlanceKey bao gồm một phương pháp tốt và hấp dẫn cho cấu hình giám sát Nagios bằng cách kích hoạt bằng cách cấu hình root và và công nhận dịch vụ tự động thay đổi thay vì sử dụng Nagios và dữ liệu cấu hình, hỗ trợ cho các hợp đồng mỗi máy chủ một lần mỗi khoảng thời gian kiểm tra, cũng như hỗ trợ việc gửi kết quả kiểm tra Nagios, tiết kiệm nhiều tài nguyên trên máy khách và máy chủ hệ thống.

Check_MK Cung cấp hệ thống thông báo linh hoạt và đơn giản mà có thể dễ dàng cấu hình. Hệ thống thông báo hỗ trợ xác định và cấu hình của nhiều kênh cho người dùng khác nhau, nhưng người dùng cũng có thể cấu hình các hệ thống thông báo Themselves.Supports DevicesAnother di động tính năng thú vị là khả năng sử dụng các ứng dụng trực tiếp từ một thiết bị di động. Nó cho phép người dùng thiết bị di dộng để dễ dàng truy cập dữ liệu trạng thái.
## Các thành phần có trong Check_MK
### Round Robin Database(RRD)
* Đây là dạng DB mặc định mà Check_MK dùng để lưu trữ dữ liệu thông tin
* Thông tin của DB được lưu trữ dưới dạng bảng và cột để lưu trữ dữ liệu
* Có thể hợp nhất được dữ liệu của một khoảng thời gian lại vào làm một.
* Có thể truy vấn được dữ liệu trong RRD bằng LiveStatus Language
* Lưu ý ngôn ngữ truy vấn này phân biệt chữ hoa và chữ thường
* Có thể sử dụng các Header để lọc thông tin hiển thị từ các truy vấn được sử dụng
* Khi dữ liệu được ghi đầy thì nó sẽ được ghi đè lên dữ liệu cũ

## Site
* Để có thể thực hiện giám sát thì cần tạo ra một site để có thể sử dụng
* Một server có thể tạo được nhiều site
* Để đăng nhập được vào site thì cần có user để đăng nhập, Chia làm 3 loại:
    * Administrator
    * Guest 
    * Normal monitoring

* Có 2 User mặc định có quyền Administrator là omdadmin và cmkadmin
* Site là cách gọi của sản phẩn được tạo ra từ nhiều Multisite

## Multisite
**Check_MK** tận dụng sự trực quan của multisite web **GUI**(The graphical user interface) để hiển thị thông tin giám sát. Multisite dựa trên livestatus vì thế nó cực kỳ nhanh và nhanh và nhạy trong các cài đặt lớn.

Multisite mang đến nhiều tính năng như:
- Lượt xem xác định của người dùng.
- Hỗ trợ giám sát phân tán qua livestatus
- Tùy chỉnh sidebar với nội dung động
- Tự động hóa và dịch vụ Web (API)
- Bảng điều khiển (Dashboards) 
- Localization
**Giao diện web** 
* Sử dụng để xem thông tin và kiểm soát hệ thống giám sát.
* Kết hợp WATO để có thể hỗ trợ cấu hình bằng website 
* WATO là tập hợp nhiều modules được sử dụng để cấu hình cho Check_MK server 
* Mỗi khi có thay đổi cần chọn cập nhật thay đổi
* Có sẵn các agent giám sát được lưu trữ và hiển thị sẵn trên web
* Có phiên bản tối ưu hóa trên điện thoại
**Views**

Multisite cho phép mỗi người dùng tùy chỉnh các chế độ xem dựng sẵn hoặc các chế độ xem dựng sẵn hoặc tạo các chế độ xem hoàn toàn mới. Điều này được thực hiện trong GUI bằng cách kết hợp linh hoạt các nguồn dữ liệu, bố cục, bộ lọc, sắp xếp, nhóm, vẽ theo cột và xem liên kết. Ý tưởng đằng sau là, các quản trị viên của hệ thống giám sát sẽ có thể tạo các chế độ xem tùy chỉnh cho người dùng hoặc khách hàng của họ, trong khi những người được trình bày một GUI càng đơn giản các tốt.

Các yếu tố của chế độ xem như bố cục, bộ lọc, v.v có thể được mở rộng thông qua Python bằng cách sử dụng khái niệm Plugin

**Distributed monitoring** (giám sát phân tán)-

Giám sát phân tán là cực kỳ hữu ích trong nhiều tình huống. **Check_MK** cho phép xem dữ liệu tập chung cũng như sao chép dữ liệu đến các trang web từ xa.
## Livestatus 
* Là một phần quan trọng trong Check_MK. Nó giúp Check_MK truy xuất dữ liệu một cách nhanh chóng
* Livestatus sẽ sử dụng Socket để lấy dữ liệu để trả lời truy vấn do đó tốc độ truy vấn của nó không còn phụ thuộc vào tốc độ I/O như là lưu dữ liệu trong File.
* Khi truy xuất dữ liệu bằng Command line thì Livestatus sẽ phân biệt chữ hoa chữ thường.
* Livestatus sẽ sử dụng Socket để check dữ liệu do đó công việc được phân đều cho các CPU

### Các thành phần phụ trợ
+ Check_MK BI - công cụ phân tích tác vụ / quy trình nghiệp vụ (dựa trên quy tắc, nếu bạn xác định quy tắc cho "tất cả máy chủ" và bạn thêm máy chủ mới, quy tắc cũng áp dụng ngay cho máy chủ đó).

+ WATO - giao diện quản trị web cho cấu hình check_mk (và nagios) (dựa trên quy tắc)

+ Event Console - giao diện xử lý sự kiện dựa trên quy tắc để xử lý dữ liệu tức là đến từ SNMP Traps hoặc Syslog. 

Ckeck_MK là phần mở rộng của hệ thống giám sát Nagios cho phép tạo cấu hình dựa trên quy tắc bằng Python