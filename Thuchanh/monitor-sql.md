# Giám sát MySQL

MySQL là hệ quản trị cơ sở dữ liệu mã nguồn mở được nhiều đơn vị sử dụng. Nó vô cùng quan trọng trong việc đọc ghi dữ liệu khác. Chính vì vậy giám sát MySQL là một việc vô cùng quan trọng

## Chuẩn bị 
Mô hình

![Imgur](https://i.imgur.com/O6Zzq0H.png)

Trước tiên bạn phải cài đặt CheckMK Agent trên máy chủ đang chạy dịch vụ MySQL. [Tại đây](Setup-agent.md)

## Cấu hình MySQL
Thực hiện câu lệnh trên máy Server có cài MySQL:

Bạn cần tạo một user MySQL dùng cho việc giám sát


Đăng nhập vào Cơ sở dữ liệu :

`mysql -u root -p`

MariaDB [(none)]> GRANT SELECT, SHOW DATABASES ON *.* TO 'usermonitor'@'localhost' IDENTIFIED BY 'passwdmonitor';

Khai báo thông tin của user dùng để giám sát vào file `mysql.cfg`

```
cat <<EOF > /etc/check_mk/mysql.cfg
[client]
user=usermonitor
password=passwdmonitor
EOF
```

Thay đổi quyền cho file vừa tạo để chắc chắn rằng nếu không phải user root thì sẽ không được phép sửa file

`chmod 700 /etc/check_mk/mysql.cfg`

## Copy file plugin từ checkmk server sang máy chủ mysql

Thực hiện câu lệnh tại máy CheckMK server:

Truy cập vào CheckMK server để copy file plugin giám sát sang bên máy đang chạy mysql 

```
scp /opt/omd/versions/1.6.0p14.cre/share/check_mk/agents/ugins/mk_mysql root@10.10.34.115:/usr/lib/check_mk_agent/plugins
root@10.10.34.115's password:
mk_mysql                                      100% 2814   455.1KB/s   00:00
```

* `10.10.34.115`: Địa chỉ IP của máy CheckMK server 
* `/usr/lib/check_mk_agent/plugins`: địa chỉ thư mục muốn sao chép tệp tin đến

## Thực hiện thêm Service trên Web IU

Truy cập web UI để thực hiện Discovery các dịch vụ

Từ **WATO** chọn `Hosts` -> `Discovery`

![Imgur](https://i.imgur.com/Cf0ZjNq.png)

Thực hiện Discovery để thêm giám sát dịch vụ mới được thêm vào

![Imgur](https://i.imgur.com/mj8sNzk.png)

Sau khi finish xong thực hiện back để thay đổi kích hoạt

![Imgur](https://i.imgur.com/uK2aJeZ.png)

Thực hiện thay đổi

![Imgur](https://i.imgur.com/VxxuG3I.png)

Thực hiện kích hoạt

![Imgur](https://i.imgur.com/gTujgRc.png)

Kiểm tra lại tại service

![Imgur](https://i.imgur.com/fV7iN4Y.png)

Thực hiện check cảnh báo

![Imgur](https://i.imgur.com/T8rAsBu.png)



