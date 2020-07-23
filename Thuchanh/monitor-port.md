# Giám sát port TCP bằng CheckMK

Port là một thuật ngữ chuyên ngành được sử dụng phổ thông trong network, system nói riêng và hệ thống nói chung. Đối với một dịch vụ được thiết kế chạy trên một số port có hiệu khác nhau. Phân loại thành 2 loại phổ biến dựa trên giao thức mà hai port đó sử dụng là TCP hay UDP

Mỗi dịch vụ sẽ chạy trên một dịch vụ khác nhau, Chính vì vậy muốn biết được dịch vụ có chạy ổn định không, có đang hoạt động chính xác cho phép mở kết nối tới client hay không đơn giản là giám sát trạng thái của các port. 

Sau đây là hướng dẫn dẫn thiết lập giám sát TCP port sử dụng CheckMK

## Cài đặt

Truy cập trang web UI để thực hiện trên WATO 

Chọn **Host & Service Parameters** -> **Active checks**

![Imgur](https://i.imgur.com/HwR0H8b.png)

Chọn **Check connecting to a TCP port**

![Imgur](https://i.imgur.com/x5JEUly.png)

Tạo Rule cho thư mục host muốn giám sát port 

![Imgur](https://i.imgur.com/28DHWT1.png)

Điền thông tin cho Rule

![Imgur](https://i.imgur.com/tdlwDnJ.png)

Điền thông tin port 

![Imgur](https://i.imgur.com/OdrF08O.png)

Điều kiện áp dụng rule. Bạn có thể áp dụng cho thư mục nào, những host có tag xác xịnh, những host xác định áp dụng cho thư mục nhưng bỏ qua một số host xác định. 

[Imgur](https://i.imgur.com/RhLbU0j.png)

Lưu lại

Kích hoạt thay đổi

![Imgur](https://i.imgur.com/WIi2axb.png)

Active

![Imgur](https://i.imgur.com/gT4jbaE.png)

Kiểm tra lại dịch vụ giám sát

![Imgur](https://i.imgur.com/dYpreGm.png)

>**Tùy chọn**: Một số tùy chọn Check kết nối đến một TCP port

![Imgur](https://i.imgur.com/vgQ07bi.png)

* Service description: mô tả dịch vụ của port này
* DNS hostname: sử dụng domain thay vì IP theo mặc định
* Expected response time: xác đinh thời gian response để xác định trạng thái OK hay Warning hoặc Critical
* Seconds before connection times out: Xác định thời gian trước khi kết nối times out.
* State for connection refusal: Trạng thái nếu kết nối bị từ chối
* Strings to expect in response: Chuỗi mong muốn trong kết quả trả về
* Maximum number of bytes to receive: Số byte lớn nhất có thể nhận
* Use SSL for the connection: Sử dụng SSL cho kết nối