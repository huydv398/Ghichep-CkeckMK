# Hoạt động cơ bản
![Imgur](https://i.imgur.com/SJ9Klce.png)

Trung tâm chính của nó Monitoring Core (Nagios/Icinga) được kết nối với 2 Module chính: **LiveStatus** và **LiveCheck**

## LiveStatus

* Sử dụng **Multisite** hỗ trợ giám sát phân tán bằng một cách hiệu quả nhất. Hiển thị data lên GUI, Mobile hay một app tùy chỉnh.

### Trước khi có LiveStatus 
* Kết quả giám sát được sẽ lưu trong file *status.dat* gây nên hiện tượng nút thắt cổ chai cho **CPU** và **Disk I/O**
* Trạng thái của file status không phải là real-time mà update ít nhất là 10 giây
* **NDOUtils** sử dụng ***database*** để theo dõi kết quả (MySQL hoặc PostgreSQL), nhưng vẫn còn một số thiếu sót quan trọng.
* Việc cài đặt **NDOUtils** khá phức tạp
* **NDOUtils** cần một database cho việc lưu trữ dữ liệu. Hơn nữa, việc dữ liệu trong database tăng lên một cách nhanh chóng khiến cho bạn phải tiêu tốn nhiều CƠU chỉ để cập nhật database.
* Việc dọn dẹp database có thể khiến Nagios bị treo trong một khoảng thời gian nhất định.

### Sau khi có LiveStatus
* **LiveStatus** cũng sử dụng ***Nagios Event Broker API*** như **NDO**, nhưng nó sẽ không chủ đọng ghi dữ liệu ra. Thay vào đó, nó sẽ mở ra một socket để dữ liệu có thể được lấy ra theo yêu cầu
* **LiveStatus** tiêu tốn ít CPU
* **LiveStatus** không làm cho **Disk I/O** thay đổi khi truy vấn trạng thái dữ liệu

## Livecheck 
Trong *Nagios 4.0* ngay cả một hệ thống hoàn hảo hiếm khi quản lý để thực hiện hơn một vài nghìn kiểm tra mỗi phút.

Trong hệ thống lớn, tỷ lệ check tối đa sẽ trở lên rất tệ. Càng nhiều máy chủ và dịch vụ thì đồng nghĩa thời gian check sẽ phải tăng lên.

Mỗi lần check tạo ra một bản **Fork**. Quá trình **Fork** rất tốn kém ngay cả khi tối ưu hóa 

Quá trình **Fork** trong Nagios Core không phân tán ra nhiều CPU mà thực hiện trên chỉ một CPU đơn. Điều này dẫn tới giới hạn số lần check mỗi giây, trong khi phần lớn các CPU khác rảnh rỗi

Livecheck khắc phục nhược điểm:

* Livecheck sử dụng các **Helper Process**, Các core giao thiếp với **helper** thông qua **Unix socket**(Điều này không xảy ra trên file System)
* Chỉ có một **Helper program** được phan tán trên tất cả các Cpu thay vì chỉ một như trước
* **Process** VM size tổng chỉ khoảng 100KB
* Việc thực hiện **Check_icmp** sẽ chomotj con số cải tiến cụ thể. Giả sử nhếu sử dụng CPU Sual Core 2800MHz CPU: trước đây sẽ là 300 ICMP check/second, sau khi cải tiến 2600 ICMP check/second


