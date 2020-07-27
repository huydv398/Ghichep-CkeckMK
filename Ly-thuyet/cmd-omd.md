# Một số lệnh OMD-CheckMK

Tạo Site

`omd create name_site`

`omd start name_site`

Ví dụ tạo một Site với tên huydv

![Imgur](https://i.imgur.com/XvpYC6U.png)

Sudo vào Site

`su - name_site`

Start Site

`omd start`

Stop Site 

`omd stop`

Bật hoặc tắt 1 service 

```
omd stop apache 
omd reload apache 
```

Kiểm tra status của các service 

`omd status`

Xóa 1 Site

`omd rm name_site`

Lệnh trên sẽ hỏi lại có xóa chắc chắn xóa hay không. Nếu muốn xóa mà không hỏi lại sử dụng option `-f`

Cấu hình các thành phần:

`omd config`

Câu lệnh sẽ hiển thị GUI

![Imgur](https://i.imgur.com/gZ2boxG.png)

Show cấu hình của site

`omd config show`

```
OMD[cmk]:~$ omd config show
ADMIN_MAIL:
APACHE_MODE: own
APACHE_TCP_ADDR: 127.0.0.1
APACHE_TCP_PORT: 5000
AUTOSTART: on
CORE: nagios
LIVESTATUS_TCP: off
MKEVENTD: on
MKEVENTD_SNMPTRAP: off
MKEVENTD_SYSLOG: off
MKEVENTD_SYSLOG_TCP: off
MULTISITE_AUTHORISATION: on
MULTISITE_COOKIE_AUTH: on
NAGIOS_THEME: classicui
NSCA: off
PNP4NAGIOS: on
TMPFS: on
```

Copy Site

`omd cp site_old site_new`

Chỉ đươc copy khi file đã được stop

Một số Option
* `--no-rrds`: Bỏ qua dữ liệu RRD
* `--no-logs`: không copy log
* `-N`: Bao gồm cả 2 option trên

Renanme Site

`omd mv name_site_old site_new`

Show những thay đổi so với cấu hình ban đầu

`omd diff`

Hoặc có thể kiểm tra 1 thư mục 

`omd diff etc/apache`

Xem chi tiết thay đổi trong file

`omd diff etc/apache/apache.conf`

Backup Site

`omd backup /tmp/mysite.tar.gz`

File sẽ được lưu vào hệ thống tại thư mục */tmp/mysite.tar.gz*

Chuyển file backup sang server muốn restore ( server đã cài checkMK)

`root@linux# omd restore /var/backups/mysite.tar.gz`

Hoặc restore với một tên khác

`root@linux# omd restore mysite2 /var/backup/mysite.tar.gz`