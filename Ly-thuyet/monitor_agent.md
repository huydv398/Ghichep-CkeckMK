# Monitoring Agent 

## Giới thiệu

Để hệ thống giám sát nhận nhiều thông tin hơn từ điểm cuối ngoài mục đích có thể truy cập được, cần có sự trợ giúp từ hệ thống đính. 

Có những tình huống không cần cài đặt Agent bổ sung- vì một Agent có thể sử dụng có sẵn. Ví dụ tất cả các thiết bị mạng đều có quản lý Agent có sẵn tích hợp SNMP

Giám sát các dịch vụ mạng- một ứng dụng web có thể truy cập qua HTTP và được theo dõi qua một kết nối. Trong trường hợp này thường có một Agent bổ sung được sử dụng để cung cấp thêm dữ liệu cho máy chủ CheckMK giám sát.

Bảng sau đây là bốn cách khác nhau mà CheckMK có thể truy cập dịch vụ cần đươc giám sát:

![Imgur](https://i.imgur.com/Fm3EH4z.png)

![Imgur](https://i.imgur.com/swKK4Gp.png)


## [Tải xuống và cài đặt Agent](Thuchanh/Setup-agent.md)

## Cấu hình thông qua RULE

Cấu hình của Agent có thể được thay đổi- trong checkMK thông qua các RULE. Chúng cung cấp cho bạn khả năng thay đổi các máy chủ khác nhau với các cài đặt hoặc bổ sung khác nhau. Thông qua rule bạn có thể liệt kê các danh sách rule sets thông qua các agent

Ví dụ: Giới hạn danh sách địa chỉ IP được phép truy cập vào agent.

Chọn **Rulesets**

![Imgur](https://i.imgur.com/kzr65rI.png)

Tìm rule cần thay đổi

![Imgur](https://i.imgur.com/ABDGHRm.png)

Tạo rule

![Imgur](https://i.imgur.com/vIqwUJg.png)

Điền thông tin cho Rule và lưu lại

Kích hoạt thay đổi

Trong WATO cũng có thể dễ dàng truy cập các gói agent của máy chủ thông qua Detail and the ***Monitoring Agent*** 

Các Agent của Linux/Unix

![Imgur](https://i.imgur.com/l7AEqgm.png)

Các agent Plugin cho Linux Unix

![Imgur](https://i.imgur.com/GafJiCm.png)

## Plug-ins

Nhiều RULE liên quan đến việc cài đặt các Plugin khác nhau. Chúng mở rộng các Agent để theo dõi các thành phần cụ thể. Hầu hết trong số này là các ứng dụng đặc biệt như Database, Ví dụ RULE giám sát MySQL :

![Imgur](https://i.imgur.com/iZPj4Q6.png)


