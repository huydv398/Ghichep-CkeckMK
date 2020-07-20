# Tìm hiểu về các thuật ngữ trong Check_mk

Khi điều kiện của máy chủ thay đổi,

![Imgur](https://i.imgur.com/YZCPvtD.png)

Khi trạng thái của máy thay đổi từ Up -> Down

## States and events

Sự khác biệt cơ bản giữa trạng thái và sự kiện

* **Event**- Sự kiện là cái gì đó xảy ra duy nhất tại thời điểm cụ thể. Các sự kiện là sự xuất hiện tự phát
* **States** - Trạng thái mô tả một tình huống duy trì. Ví dụ ổ cứng X đang trực tuyến. Để quan sát, hệ thống phải luôn tham dò thường xuyên.

Trong giám sát thường có thể chọn làm việc với các sự kiện hoặc với các trạng thái.

CheckMK có thể đáp ứng cả trạng thái và sự kiện, nhưng ưu tiên giám sát dựa trên trạng thái

Một số lợi thế của phương pháp:
* Thường Xuyên kiểm tra trong một khung thời gian nhất định cho phép thu thập dữ liệu hiệu suất để ghi lại lịch sử thời gian.
* CheckMK có thể kiểm soát tốc độ các trạng thái. Không có rủi ro từ một sự tấn công trong các tình huống lỗi chung.
* Trong tình huống mất kiểm soát- ví dụ sự cố mất điện tại một trung tâm máy tính - Luôn có trạng thái tổng thể tin cậy.

## Hosts and Service 
### Hosts
* Một máy chủ
* Một thiết bị mạng (switch, router, loand balancer)
* Một thiết bị đo lường có gắn địa chỉ IP
* Mọi vật được gắn địa chỉ IP
* Một cụm gồm nhiều máy chủ
* Một máy ảo

#### Các trạng thái Hosts 
* **UP**(Xanh lá): Máy chủ có thể truy cập qua mạng
* **Down**(Màu đỏ): Các máy không trả lời các yêu cầu mạng, không thể truy cập.
* **UNREACH**(Màu cam): Đường dẫn đến máy chủ hiện bị chăn để theo dõi, bởi vì bộ định tuyến hoặc chuyển đổi trong đường dẫn đã bị lỗi
* **PEND**(Màu xám): Không thực sự là một điều kiện để giám sát.

## Parents 

Để giám sát có thể đánh giá trạng thái (UP, DOWN, UNREACH, PEND) nó phải biết thông qua đường dẫn nào mà mọi máy chủ cá nhân có thể đạt được.

## Services - Dịch vụ

Một máy chủ lưu trữ có một số dịch vụ. Một dịch vụ có thể là bất cứ điều gì. Một dịch vụ là bất kỳ một thành phần hoặc khía canh của host có thể **OK** hoặc **Not OK**. Đương nhiên, trạng thái chỉ có thể được xác định nếu máy chủ ở trong điều kiện **UP**.

![Imgur](https://i.imgur.com/yYscYfd.png)

Khi xác định điều kiện nào là "xấu hơn", Checkmk sử dụng trình tự sau:

* **OK** -> **WARN** -> **UNKNOWN** -> **CRIT**

## Nhóm host và service 

Host và dịch vụ có thể được nhóm lại để có cái nhìn tổng quan. Theo cách này, một máy chủ hay dịch vụ có thể ở nhiều nhóm. Các nhóm này hoàn toàn là tùy chọn và không cần thiết cho cấu hình. Các nhóm máy chủ có thể hữu ích khi bên cạch cấu trúc thư mục mà các máy chủ được quản lý, nhóm bổ sung được mong muốn.

## Contacts and contact groups

Contacts and contact groups cung cấp khả năng phân công người cho máy chủ dịch vụ. Một liên hệ tương đồng với một tên người dùng hoặc giao diện web.

Người dùng cũng có thể gán cho nhiều nhóm liên hệ.

Ví dụ:

* Ai được phép xem một cái gì đó?
* Ai được phép cấu hình và kiểm soát dịch vụ nào?
* Ai nhận được thông báo cho vấn đề nào?

User ***cmkadmin***, người được xác định tự động bằng cách tạo ra một ví dụ, luôn được phép xem tất cả các máy chủ và dịch vụ nhay cả khi chúng không phải là một liên hệ. Điều này được xác định thông qua vai trò là quản trị viên của họ.

### Người dùng và vai trò

Trong khi những người chịu trách nhiệm hoặc ủy quyền cho một máy chủ hoặc dịch vụ cụ thể được xác định thông qua các liên hệ và nhóm liên hệ, các đặc quyền của họ được kiểm soát thông qua vai trò. Checkmk được cung cấp 3 vai trò từ đó các vai trò khác có thể được bắt nguồn sau này. Mỗi vai trò xác định một loạt các quyền có thể được tùy chỉnh. Các vai trò tiêu chuẩn có các ý nghĩa sau:
* **Admin**: Có thể xem tất cả, có tất cả các đặc quyền.
* **User** : Chỉ có thể xem rằng họ là một **contact**. Có thể quản lý máy chủ trong các thư mục được gắn cho User. Không được phép thực hiện cài đặt chung.
* **Guest**: Có thể xem tất cả, nhưng có thể không cấu hình và có thể không ảnh hưởng đến giám sát.
### Vấn đề, sự kiện và thông báo
#### Vấn đề xử lý và xử lý

CheckMK xác định mọi máy chủ và mọi dịch vụ **UP** or **DOWN** là một vấn đề. 
* Một vấn đề có thể có 2 trạng thái: **Unhandled** (chưa xử lý) và **handled** (xử lý)

![Imgur](https://i.imgur.com/4VjbNPJ.png)

Thủ tục : Một vấn đề mới chưa được xứ lý
* Có user xác nhận vấn đề thì nó sẽ được gắn cờ là xử lý.
* Những vấn đề chưa giải quyết là những vấn đề mà không ai tham gia.

### Alerts and notifications
Cảnh báo và thông báo

Khi điều kiện của máy chủ thay đổi, (ví dụ: từ **OK**-> **CRIT**), CheckMK đăng ký một **Event**. Những sự kiện này có thể hoặc không thể tạo ra một thông báo. CheckMK được thiết kế đến mức bất cứ khi nào máy chủ hoặc dịch vụ gặp sự cố Email sẽ được gửi đến các Contact của đối tượng(Có thể được tùy chỉnh rất linh hoạt)

Cảnh báo cũng phụ thuộc vào một số tham số. Nó đơn giản khi chúng ta xem xét các trường hợp mà thông báo *không được gửi*. 

Thông báo bị bãi bỏ:
* Khi thông báo đã hủy kích hoạt trên global trong master control
* Khi thông báo đã hủy kích hoạt trong host/services 
* Khi thông báo bị hủy kich hoạt cho một trạng thái cụ thể của máy chủ/services (ví dụ: không có thông báo nào cho **WARN**)E
* Khi các sự cố ảnh hưởng đến dịch vụ có máy củ là **DOWN** hoặc **UNREACH**

## Flapping Service và hosts
Đôi khi xảy ra một dịch vụ liên tục và nhanh chóng thay đổi tình trạng của nó. Để tránh thông báo liên tục, CheckMK chuyển dịch vụ sang trạng thái Flapping. Một thông báo sẽ được tạo ra để thông báo cho người dùng về sự thay đổi và im lặng của cảnh báo. 

Sau một thời gian thích hợp, nếu không có thay đổi nhanh nào sảy ra, và trạng thái cuối cùng(tốt hoặc xấu) là chuẩn, thì trạng thái flapping sẽ mất và cảnh báo bình thường trở lại.

## Thời gian chết theo lịch trình

Khi muốn tạm ngừng thông báo khi bảo trì hoặc các vấn đề xuất hiện trong giám sát trong thời gian này có thể tạm thời bị bỏ qua.

## Timeperiods - Khoảng thời gian

Timeperiods xác định các khoảng thời gian thường xuyên, định kỳ hàng tuần được sử dụng ở các vị trí khác nhau trong cấu hình của giám sát.

Một số tình huống quan trọng sử dụng khoảng thời gian:
* Giới hạn thời gian trong đó thông báo sẽ được thực hiện(thời gian thông báo)
* Giới hạn thời gian thực hiện kiểm tra (Thời gian kiểm tra)
* Thời gian phục vụ cho việc đánh giá tính khả dụng (Thời gian phục vụ)
* Thời gian trong đó bảng điều khiển sự kiện sẽ áp dụng quy tắc xác định

## Tổng quan về các biểu tượng máy chủ và dịch vụ quan trong nhất

![Imgur](https://i.imgur.com/Fj7rR8v.png)

