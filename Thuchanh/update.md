# Update Version cho Check_mk

![Imgur](https://i.imgur.com/atvyQNc.png)

Hiện tại đang dùng là bản Raw 1.6.0p10

Tải bản mới nhất tại đây: 

https://checkmk.com/download-archive.php

![Imgur](https://i.imgur.com/NODlCAQ.png)

Chọn Phiên bản đang sử dụng, Ở đây tôi sử dụng Bản RAW 

Chọn Raw:

Chọn phiên bản hệ điều hành đang sử dụng:

![Imgur](https://i.imgur.com/287jPus.png)

Copy Link Download :

## Cài đặt trên Máy chủ Check_MK

Tới máy chủ và tải về

![Imgur](https://i.imgur.com/QrI490V.png)

Thực hiện Cài đặt

`# yum install -y check-mk-raw-1.6.0p14-el7-38.x86_64.rpm`

Kiểm tra Version

![Imgur](https://i.imgur.com/O4R5NbL.png)

```
[root@cmk-server ~]# omd version cmk
OMD - Open Monitoring Distribution Version 1.6.0p10.cre
```

```
omd stop cmk
omd update cmk
```



![Imgur](https://i.imgur.com/3GEiF56.png)

Chọn <Update!> 

`omd start cmk`

Kiểm tra trên Web 

![Imgur](https://i.imgur.com/hZVZMCT.png)

>**Lưu ý**: Khi update lên 1.6 phần thiết lập cảnh báo qua telegram sẽ bị mất bạn phải config lại

Như vậy đã thành công Việc Update lên Bản Raw 1.6.0p14

