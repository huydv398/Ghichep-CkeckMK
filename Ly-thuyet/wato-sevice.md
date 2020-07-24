# Hiểu và cấu hình dịch vụ

## 1. Giới thiệu

Service thực chất là "substance-nội dung" của một hệ thống giám sát. Mỗi cái đại diện cho một mắt xích quan trọng trong hệ thống giám sát CNTT phức tạp của bạn. Tính hữu ích hoàn toàn tăng hay giảm tùy thuộc vào mức độ chính xác và hữu ích của các dịch vụ đã được cấu hình. Cuối cùng, Việc giám sát nên thông báo một cách đáng tin cậy bất khi nào một vấn đề trở nên rõ ràng ở đâu đó, nhưng chắc chắn cũng nên giảm thiểu các thông báo sai hoặc không các tác dụng.

CheckMK chứng tỏ sức mạnh lớn nhất của nó khi cấu hình service- Nó sở hữu một hệ thống không thể so sánh và vô cùng mạnh mẽ phát hiện tự động và cấu hình các service cảnh báo. Với CheckMK, không cần xác định từng dịch vụ thông qua các mẫu và phân tán riêng lẻ. CheckMK có thẻ tự đọng và đáng tin cậy phát hiện danh sách các dịch vụ được theo dõi. Nó đảm bảo những thay đổi hàng ngày trong một trung tâm xử lý luôn được bảo vệ kịp thời và không có dịch vụ quan trọng nào không được giám sát.

Cách thức hoạt động: Kiểm tra tham số/ các ngưỡng cảnh báo cho các dịch vụ riêng lẻ - được cấu hình độc lập thông qua các rule. 

## 2. Host service in WATO 
### 2.1 Kết hợp một máy chủ mới

Khi thêm một máy chủ mới trong WATO, bước tiếp theo là gọi ra danh sách các dịch vụ. Với hành động này, việc phát hiện dịch vụ trong lần đầu tiên cho máy chủ.  

* ![Imgur](https://i.imgur.com/kboWPzy.png) ***Service & go to Service*** 

Thêm dịch vụ mới

![Imgur](https://i.imgur.com/dn1wMIo.png)

Chọn dịch vụ cần giám sát

![Imgur](https://i.imgur.com/61O8cSO.png)

![Imgur](https://i.imgur.com/USSELhy.png)

![Imgur](https://i.imgur.com/teWVuzQ.png)

![Imgur](https://i.imgur.com/Epi1QjV.png)

### 2.2 Thêm các dịch vụ

[Imgur](https://i.imgur.com/d7XdYhy.png)

Chọn Service -> Monitor. Kích hoạt lại các thay đổi

### 2.3 Loại bỏ các dịch vụ không mong muốn

#### Tạm thời vô hiệu hóa
![Imgur](https://i.imgur.com/2EpNli0.png)

Đưa các Service tạm thời không giám sát ra ngoài phạm vi

#### Vô hiệu hóa vĩnh viễn 

#### Làm mới dịch vụ

![Imgur](https://i.imgur.com/qgbtC6p.png)

Tất cả các dịch vụ của máy chủ sẽ được làm mới và được xác định mới. 

## 3. Bulk Discovery - Discovery đồng thời trên nhiều máy chủ

![Imgur](https://i.imgur.com/VexuPBM.png)

![Imgur](https://i.imgur.com/OuAKeiL.png)

Với biến thể bên thứ 3, bạn cũng có thể thực hiện khám phá dịch vụ theo các đệ quy trong tất cả thư mục con. Trong tất cả các tùy chọn, bước tiếp theo sẽ đưa bạn đến màn hình làm việc sau:

![Imgur](https://i.imgur.com/CAvOPvc.png)


* `Add unmonitored services and new host labels`: Thêm dịch vụ không được giám sát và lables host mới
* `Remove vanished services` : Xóa hết các dịch vụ vanished(đã mất)
* `Add unmonitored services and new host labels, remove vanished services`: Thêm dịch vụ không được giám sát và nhãn máy chủ mới, xóa dịch vụ đã biến mất 
* `Refresh all services (tabula rasa), add new host labels`: Làm mới tất cả các dịch vụ (tabula rasa), thêm nhãn máy chủ mới


Trong chế độ này, Bulk Discovery sẽ tìm thấy chính xác các tùy chọn giống như trong danh sách dịch vụ WATO

Trong phần Selection, lựa chọn hợp lý cho host. 

* `Only include hosts that failed on previous discovery`: chỉ cho phép Discovery lặp lại cho các máy không thành công trước đó.
* `Only include hosts with a failed discovery check`: 
* `Exclude hosts where the agent is unreachable`: Bỏ qua các máy mà có thời gian truy cập vượt mức để discovery vào các máy tiếp theo

## 4. Kiểm tra thông số Check parameters in services

Có nhiều Check-Plugin có thể được cấu hình bằng parameterst. Phổ biến nhất là ngưỡng cài đặt: 

![Imgur](https://i.imgur.com/7gfYUB2.png)

Check Parameters cho một dịch vụ bao gồm ba phần:

1. Mỗi **plug-in** đều có một **Default value** cho *Parameter*.
2. Một số Plugin được cài đặt trong khi Discovery 
3. Parameters có thể được cài đặt thông qua các Rule

## 5. Tùy chỉnh The Service discovery 
Tất cả các bộ quy tắc có liên quan đến Service Discovery có thể được thấy trong 

**Host & Services parameters** -> **Parameters for discovered services**

![Imgur](https://i.imgur.com/GFYskuD.png)

### 5.1 Giám sát Process

Có hàng trăm tiến trình đang chạy trên một máy chủ linux.

Đối với dịch vụ giám sát, bạn cần phải làm **Manual check** hoặc sử dụng Rule set **Process discovery** để báo cho service discovery cần xử lý.

### 5.2 Monitoring of switch ports
Checkmk sử dụng logic để giám sát network interfaces trên servers và Port trên thiết bị ethernet switches. 

## 6. Giám sát thủ công Manual check
Trong Discovery, có một số tình huống là dịch vụ discovery tự động sẽ không có ý nghĩa. 

## 7 The discovery check

### 7.1 Tự động kiểm tra các dịch vụ không giám sát

Dịch vụ này tồn tại cho mọi máy chủ và sẽ ghi lại cảnh báo mỗi khi tìm thấy các dịch vụ không được giám sát:

![Imgur](https://i.imgur.com/gxtuaVw.png)

Chi tiết về các dịch vụ không được giám sát hoặc biến mất có thể tìm thấy trong **Long output of check plugin** của chi tiết dịch vụ:

### 7.2 Thêm dịch vụ tự động
Discovery có thể thêm dịch vụ còn thiếu, Kích hoạt tùy chọn *Automatically update service configuration* 

Trong chế độ bạn cũng có thể xóa các dịch vụ không cần thiết hoặc thậm chí xóa tất cả các dịch vụ hiện có và thực hiện Discovery mới(Refresh). Cả hai tùy chọn đều nên sử dụng cẩn thận.

## 8. Passive services 
Dịch vụ thụ động là dịnh vụ không được checkMK khởi xướng tích cực, thì vì kiểm tra kết quả thường xuyên được chuyển từ nguồn bên ngoài. Điều này thường xảy thông qua command PIPE. Dưới đây là quy trình từng bước tạo dịch vụ thụ động:

Bạn cần thông báo cho core của dịch vụ. 

![Imgur](https://i.imgur.com/4xnZLJQ.png)

## 9. Các nhóm dịch vụ trong WATO_Service 

### Tạo nhóm dịch vụ

Các dịch vụ có thể được tìm thấy **WATO** -> **Host & Service Groups**-> New host group


![Imgur](https://i.imgur.com/H4zdSMB.png)

### Thêm dịch vụ vào nhóm dịch vụ

Để gắn các dịch vụ cho các nhóm dịch vụ, bạn cần 1 **Rulesets** 