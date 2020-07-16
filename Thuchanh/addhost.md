# Hướng dẫn add host để Check_MK giám sát

Làm thế nào để add thêm một host. Để làm được điều này máy muốn giám sát phải được download và cài đặt Agent của Check_MK.

Đăng nhập vào Check_MK và làm theo hướng dẫn

### Tạo host

* Chọn **Hosts** ở mục WATO 
* Chọn **New host**

![Imgur](https://i.imgur.com/UqZc9oN.png)

* Điền thông tin của host muốn giám sát bao gồm tên địa chỉ IP của chúng. sau đó lưu và đến service 

Điền tên cho host mới:

![Imgur](https://i.imgur.com/J9FeBlU.png)

Nhập địa chỉ IP của host mới

![Imgur](https://i.imgur.com/yehnT59.png)

Lưu và test thử:

![Imgur](https://i.imgur.com/aypV6zq.png)

Ping và agent hoàn thành là OK:

![Imgur](https://i.imgur.com/LiWlqUh.png)

Save & go to Services 

![Imgur](https://i.imgur.com/2BCabzr.png)

* Đi vào bước quyết định giám sát những Service nào. Nếu muốn giám sát tất cả những Service mà check_mk phát hiện được hãy chọn Monitor không thì hãy chọn disable. Còn nếu bạn muốn loại bỏ hay giám sát 1 service riêng lẻ nào đó hãy chọn dấu X hoặc dấu tích

1: Tích để tích tất cả các Service mà check_mk tìm thấy

Monitor để giám sát

![Imgur](https://i.imgur.com/5tNvmXA.png)

Hoặc chọn Service mà muốn giám sát và chọn Monitor để giám sát

![Imgur](https://i.imgur.com/PR6OZly.png)

Chọn **Changes**

![Imgur](https://i.imgur.com/fccFDc9.png)

Chọn **Activate afected**, để kích hoạt các service.

![Imgur](https://i.imgur.com/Fvf4Gg1.png)

Nếu các service không khởi động được:

![Imgur](https://i.imgur.com/VYuazIT.png)

Click vào option:

![Imgur](https://i.imgur.com/ZJBDz9Y.png)

Chọn reschedule check

![Imgur](https://i.imgur.com/U95GgWg.png)

Như vậy đã hoàn thành add host và service cho Check_mk
