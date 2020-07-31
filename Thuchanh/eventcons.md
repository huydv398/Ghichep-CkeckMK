https://github.com/niemdinhtrong/thuctapsinh/blob/master/NiemDT/Ghichep_checkmk/docs/09.Event-console.md

# Event console 

## Giới thiệu
Ngoài việc giám sát các service thông qua các metric. CheckMK còn có một kiểu giám sát khác làm việc với sự kiện(Event). Với Envent Console, CheckMK tích hợp một hệ thống độc lập với lỗi giám sát - Event Deamon (mkeventd) được dùng để giám sát từ các sự kiện từ các nguồn như Syslog, SNMP Trap, Windows Envent Log, File Log và các ứng dụng của người dùng. Nó có thể nhận Message trực tiếp từ các nguồn như Syslog hay SNMP và dựa vào các Rule sẽ đưa ra cảnh báo

## Thiết lập
Chú ý trước khi thiết lập dừng dịch vụ

`omd stop [tên_site]`

Cho phép CheckMK nhận log từ Syslog

`omd config [option]`

option: nếu chỉ có 1 site thì ko cần option, nếu nhiều site cần thêm tên site

Chọn Addons

![Imgur](https://i.imgur.com/khKUlwj.png)

Bật `MKEVENT` và `MKEVENTD_SYSLOG` Để cho phép CheckMK nhận log từ Syslog qua port 514 UDP

![Imgur](https://i.imgur.com/07gu10h.png)

Lưu thay đổi sau đó khởi động OMD

`omd start cmk`


Bây giờ truy cập Web UI để tạo rule

Chọn `Event Console` -> New Rule Pack

![Imgur](https://i.imgur.com/NqQqqx6.png)

Điền thông tin cho Rule sau đó lưu lại

![Imgur](https://i.imgur.com/LtIgZAT.png)

Ta thấy Rule Pack vừa tạo, Tạo các Rule trong Rule Pack

![Imgur](https://i.imgur.com/KuFdj8l.png)

![Imgur](https://i.imgur.com/YEz9Ofm.png)

Điền thông tin cho rule

Phần miêu tả

![Imgur](https://i.imgur.com/ABaWUQn.png)

Điều kiện để Match Rule

![Imgur](https://i.imgur.com/yRLwbok.png)


Ở đây tôi để Failed, trong bản tin có log từ **Failed**

![Imgur](https://i.imgur.com/yRLwbok.png)

Chọn các Action khi bản tin match với rule ở trên. Ở đây tôi chỉ đặt trạng thái của envent là `WARNING`

![Imgur](https://i.imgur.com/lNwJuEk.png)

Hành động gửi cảnh báo

![Imgur](https://i.imgur.com/0CU2095.png)
Sau đó lưu lại

Bạn có thể fake một bản tin để xem rule của bạn có hoạt động đúng như mong muốn không. Khai báo các giá trị muốn fake trong trường **EVENT SIMULATOR** và chon **Try out**. Nếu thấy biểu tượng như sau thì đã match

![Imgur](https://i.imgur.com/dw59jYU.png)

## Vào server muốn thu thập log để thao tác

Cấu hình gửi log đến checkMK

`echo '*.*  @[Nhập_IP_server_CheckMK]:514;RSYSLOG_SyslogProtocol23Format' >> /etc/rsyslog.conf`

>**Chú ý**: Điền chính xác IP server CheckMK.

Restart lại rsyslog

`systemctl restart rsyslog`

Khi cho bản tin log trên client có từ Failed thì sẽ có Event trên CheckMK

![Imgur](https://i.imgur.com/64RvUSL.png)

Cảnh báo về tele:

![Imgur](https://i.imgur.com/hVfkOtX.png)
