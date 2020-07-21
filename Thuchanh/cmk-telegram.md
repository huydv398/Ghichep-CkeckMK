# Các bước setup cảnh báo Check_MK bởi Telegram

## Tạo Bot Telegram và lấy User ID

### Tạo Bot Telegram:

Tìm `botfather`:

![Imgur](https://i.imgur.com/wYgDDm1.png)

Thực hiện các bước sau:

`/newbot`

Đặt tên cho bot:

`HuyDV_NH_Test_bot`

Xác nhận: Chú ý phải có hậu tố _bot ở sau thì mới tạo được botfather

`HuyDV_NH_Test_bot`

Bạn sẽ nhận được thông tin con Bot Telegram của mình, lưu giữ lại chuỗi token.

![Imgur](https://i.imgur.com/bHVcoWl.png)

### Xác định ID user 

Để người dùng bất kỳ nào có thể được nhận cảnh báo thì user phải chat vào con bot đó và ta sẽ lấy được ID của người dùng đó để thiết lập cảnh báo lên Check_MK.

ví dụ: 

`https://api.telegram.org/bot123456782:QQERTREWQWup8OzXl6bbcNV8lBVDW6I/getUpdates`

Chú ý trước chuỗi token phải có `bot`

* Sau đó chat với bot vừa tạo 

* refresh lại trang token thì sẽ cho ta một địa chỉ id đó là Chat ID:

![Imgur](https://i.imgur.com/7huRVg4.png)

## Cấu hình Check_MK trên server 

### Tạo ra file telegram.py

Tạo file với câu lệnh:

`vi /omd/sites/[site-cmk]/share/check_mk/notifications/telegram.py`

>**Lưu ý**: Đổi tên *site* 

Thay thế token_cua_ban bằng token của bot vừa tạo. Truy cập link để lấy script cảnh báo qua telegram.

`https://paste.cloud365.vn/?d81c54e86a5a20c1#yJw1TCDmVPZMtdu2DvG00BO15tGHiJjR4EO8QpGuAO4=`


![Imgur](https://i.imgur.com/2MOATQQ.png)

* Thêm quyền thực thi cho thư mục

`chmod +x /omd/sites/[site-cmk]/share/check_mk/notifications/telegram.py`

* Restart lại omd server 

`omd restart`

### Cấu hình trên Site

Tạo `Attributes User`

* Click `User` -> `Custom attributes`

![Imgur](https://i.imgur.com/YCAyiN1.png)

* Chọn New Attributes

![Imgur](https://i.imgur.com/YB1Djki.png)

Nhập thông tin chính xác như sau

Name: `TELEGRAM_CHAT_ID`

Title: `Telegram ID`

Topic: Lựa chọn ***Identity***

* Tích chọn: 
    * Users can change this attribute in their personal settings
    * Show the setting of the attribute in the list table
    * Make this variable available in notifications

![Imgur](https://i.imgur.com/zbSHZsh.png)

Tạo thành công

![Imgur](https://i.imgur.com/qVcAau1.png)

#### Tạo User cảnh báo

Click `User` -> `New user`

![Imgur](https://i.imgur.com/nBQkcNF.png)

Điền thông tin như sau:

![Imgur](https://i.imgur.com/Ot7Z7Xw.png)

Lưu kết quả

Tạo **rule**

Chọn `Notification` -> `New Rule`

![Imgur](https://i.imgur.com/SAIvmpe.png)

Điền tên rule cảnh báo muốn tạo và chọn Telegram làm cảnh báo

![Imgur](https://i.imgur.com/qUorLo4.png)

Kích hoạt các thay đổi

![Imgur](https://i.imgur.com/ZghpH1z.png)

![Imgur](https://i.imgur.com/YLP8FL3.png)

### Test thử cảnh báo

![Imgur](https://i.imgur.com/nC6O3nc.png)

Kéo đến `VARIOUS COMMANDS` - Chọn `SEND` Đợi khoảng 1 phút để cảnh báo về telegram.

![Imgur](https://i.imgur.com/CKCFKOC.png)

Trên là quá trình tạo cảnh báo Check_MK qua Telegram
