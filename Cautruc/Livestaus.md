# LiveStauts

![Imgur](https://i.imgur.com/E6JDwod.png)

## Event Console - Điều khiển sự kiện

Với bảng điều khiển sự kiện trong Check_MK hệ thống tích hợp đầy đủ cho giám sát các sự kiện từ các nguồn như Syslog, SNMP Traps, Windows Envent Logs, Log Files and User's Application.

![Imgur](https://i.imgur.com/jDQed3X.png)

Các sự kiện không được sử lý bởi Monitoring core mà thay vào đó là dịch vụ riêng của họ- Event Deamon

Event Console có một kho lưu trữ trong đó nó có thể nghiên cứu các sự kiện trong quá khứ. Tuy nhiên, điều này không thay thế cho một kho lưu trữ nhật ký thực sự.
* Nhiệm vụ của Event Console là lọc thông minh một số lượng hạn chế các thông báo có liên quan từ một luồng lớn

* Nó được tối ưu hóa cho sự đơn giản, mạnh mẽ và thông lượng - không dành cho viêc lưu trữ khối lượng dữ liệu lớn.

Event_Console nhận tin nhắn. Tin nhắn là một dòng văn bản với một chuỗi các thuộc tính bổ sung có thể có.

Ví dụ: Time Stamp - Dấu thời gian, tên máy chủ