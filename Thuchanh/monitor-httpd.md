# Giám sát Apache 

Thực hiện giám sát một máy chủ CentOS 7 cài Web server apache httpd

## Trên máy cài Apache 

Cài đặt Apache 

`yum install -y httpd`

Dùng trình soạn thảo thêm cấu hình vào Module sau:

`vi /etc/httpd/conf/httpd.conf`

```
<IfModule mod_status.c>
<Location /server-status>
SetHandler server-status
Order deny,allow
Deny from all
Allow from 127.0.0.1 ::1
</Location>
# Keep track of extended status information for each request
ExtendedStatus On
</IfModule>
```

## Copy file bằng Plugin

Đứng tại máy CheckMK Server, thực hiện câu lệnh:

```
[root@cmk-server ~]# scp /opt/omd/versions/1.6.0p14.cre/share/check_mk/agents/plugins/apache_status root@10.10.34.115:/usr/lib/check_mk_agent/plugins
root@10.10.34.115's password:
apache_status                                 100% 7651     1.9MB/s   00:00
```

Coppy file plugin từ máy chủ omd ( `/opt/omd/versions/1.6.0p14.cre/share/check_mk/agents/plugins/apache_status` ) qua máy client (`/usr/lib/check_mk_agent/plugins/` ).

Thêm quyền được thực thi cho File:

` chmod +x /usr/lib/check_mk_agent/plugins/apache_status`

Thực hiện khởi động lại service HTTPD

`systemctl restart httpd`

## Thực hiện thêm service trên WATO

Trên **WATO** chọn `Hosts` -> `Discovery`

![Imgur](https://i.imgur.com/y9tDtVe.png)

Thực hiện Discovery để thêm giám sát dịch vụ mới được thêm vào

![Imgur](https://i.imgur.com/mj8sNzk.png)

Sau khi finish xong thực hiện back để thay đổi kích hoạt

![Imgur](https://i.imgur.com/uK2aJeZ.png)

Thực hiện thay đổi

![Imgur](https://i.imgur.com/VxxuG3I.png)

Thực hiện kích hoạt

![Imgur](https://i.imgur.com/gTujgRc.png)

Kiểm tra lại tại service

![Imgur](https://i.imgur.com/L4Yj12a.png)