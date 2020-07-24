# Các bước Giám sát Process Linux bởi CheckMK

Ngữ cảnh Sử dụng: Trong CheckMK có nhiều tiến trình Process chạy(sshd,httpd,mysql,...) có thể biết chính xác các tiến trình đó đang sử dụng thế nào ta thường xuyên sử dụng câu lệnh `ps` Cộng thêm các Option và `grep` để cho kết quả mong muốn.

CheckMK đã hỗ trợ check các thông số này thông qua kiểu manual ckeck. Dưới đây là các bước thực hiện cơ bản ví dụ để giám sát Process mysql

## Thao tác trên giao diện WATO Check_MK

Click `Manual Checks` ->` Application Processes & Services` -> `State and count of processes`

![Imgur](https://i.imgur.com/kTEOGSL.png)

Tạo rule(quy tắc) cho việc check Service 

![Imgur](https://i.imgur.com/hx813Ra.png)

Có thể thiết lập rất nhiều tham số theo kinh nghiệm của bạn.

**RULE PROPERTIES**: Mô tả chung cho rule

![Imgur](https://i.imgur.com/ll2pSIN.png)

**PARAMETERS**: Thiết lập các tham số phù hợp.

*Command regex*:  `.*usr/libexec/mysqld*`

![Imgur](https://i.imgur.com/rXNl4T5.png)

![Imgur](https://i.imgur.com/NOFuFYb.png)



Lưu lại và kích hoạt rule

