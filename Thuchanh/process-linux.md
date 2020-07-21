# Các bước Giám sát Process Linux bởi CheckMK

Ngữ cảnh Sử dụng: Trong CheckMK có nhiều tiến trình Process chạy(sshd,httpd,mysql,...) có thể biết chính xác các tiến trình đó đang sử dụng thế nào ta thường xuyên sử dụng câu lệnh `ps` Cộng thêm các Option và `grep` để cho kết quả mong muốn.

CheckMK đã hỗ trợ check các thông số này thông qua kiểu manual ckeck. Dưới đây là các bước thực hiện cơ bản ví dụ để giám sát Process httpd

Thao tác trên giao diện WATO Check_MK