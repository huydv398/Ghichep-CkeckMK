# Cài đặt giám sát HTTP

## Chuẩn bị
* CheckMK Server 
* CLient có cài Service http & agent CheckMK

`yum -y install httpd` 

or 

`apt-get -y install apache2`

## Cài đặt giám sát

Sử dụng kiểu **Active check** mà CheckMK hỗ trợ.

Chọn `Host & Service Parameters` -> `Active checks (HTTP, TCP, etc.)`

![Imgur](https://i.imgur.com/TsZfBrF.png)

Chọn `Check HTTP Service` 

![Imgur](https://i.imgur.com/oX8e9zz.png)

Tạo tùy biến **Rule** cho việc *check service HTTP*

Chọn `Create rule in folder`

![Imgur](https://i.imgur.com/r7Ad9jR.png)

**RULE PROPERTIES**: Mô tả cơ bản cho rules

![Imgur](https://i.imgur.com/kX9MEBP.png)

**CHECK HTTP SERVICE**: Tùy vào Check_MK, ở đây có những giám sát chuyên sâu về HTTP

![Imgur](https://i.imgur.com/N6MI3PD.png)


**CONDITIONS**: Là những điều kiện áp rule cho host nào, IP nào ...

![Imgur](https://i.imgur.com/msAXQRX.png)

Lưu lại các chỉnh sửa

Kích hoạt các cài đặt

![Imgur](https://i.imgur.com/0IssEbO.png)