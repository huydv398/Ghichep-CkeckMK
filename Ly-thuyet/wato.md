# Tìm hiểu về cấu hình Check_MK

## Giới thiệu 
Check_MK phân biệt giữa môi trường cấu hình mà bản quản lý máy chủ, cài đặt và giám sát thực tế trong đó giám sát hoạt động diễn ra.

Thay đổi trong cấu hình, Ví dụ: Thêm một Host mới- ban đầu sẽ không có hiệu lực trong việc giám sát. Trước tiên phải kích hoạt thay đổi, sẽ thay đổi các cài đặt mà bạn đã chọn để kích hoạt. Sau khi thêm host mới, bạn có thể muốn xác định ngưỡng hoặc  xóa một số dịch vụ trước khi chúng kích hoạt.

WATO - Công cụ quản trị web. WATO duy trì tất cả các dữ liệu ở định dạng văn bản, thông thường người dùng có kinh nghiệm có thể chỉnh sửa thủ công hoặc thậm chí tạo bằng các tệp lệnh. 

Bất cứ khi nào thực hiện thay đổi cấu hình giám sát bằng cách sử dụng WATO, thay đổi này trước tiên sẽ chọn và giữ dưới dạng chờ xử lý.

![Imgur](https://i.imgur.com/WzGGOI1.png)

4 thay đổi đang chờ xử lý.

![Imgur](https://i.imgur.com/rJn1kW8.png)

Với nút kích hoạt thay đổi `Activate afected`, dữ liệu cấu hình từ WATO sẽ được sử dụng để cấu hình mới cho monitoring core và hướng dẫn lõi bắt đầu sử dụng cấu hình mới:

![Imgur](https://i.imgur.com/kEIjZFM.png)

Danh sách các thay đổi chờ xử lý(Unhandled) sẽ bị xóa. Tuy nhiên, những mục này không bị mất - sau đó chúng có thể gọi bằng **Audit log**.

## Các module quan trọng của WATO
WATO bao gồm nhiều module- một chức năng quan trọng của Check_MK. Các module tiêu biểu sau:

![Imgur](https://i.imgur.com/pwryF45.png)

## Tất cả các công cụ quản lý và cấu hình của WATO

![Imgur](https://i.imgur.com/5gC5JZV.png)