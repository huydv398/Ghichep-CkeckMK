https://github.com/datkk06/meditech-ghichep-omd/blob/master/docs/10.1.Manage-Backup-site-on-web.md

# Backup toàn bộ cấu hình bằng câu lệnh

## Các bước tiến hành

### Backup site

* Liệt kê các site đang có trên hệ thống

```
[root@cmk-server tmp]# omd sites
SITE             VERSION          COMMENTS
cmk              1.6.0p14.cre     default version
huydv            1.6.0p14.cre     default version
```

* Dừng file muốn backup

`omd stop cmk`'

```
[root@cmk-server tmp]# omd stop cmk
Removing Crontab...OK
Stopping apache...killing 30664..........................OK
Stopping nagios....OK
Stopping npcd...OK
Stopping rrdcached...waiting for termination...OK
Stopping mkeventd...killing 30561....OK
Stopping 1 remaining site processes...OK

```

* Backup dữ liệu của site

`omd backup [tên site] /opt/[tên file backup].tar.gz`

```

omd backup cmk /opt/monitoring-bk.tar.gz
```

## Restore site 

Trên một server khác cùng cài một phiên bản, Restore lại site

* Copy file backup vào server mới
* Tiến hành kiểm tra trạng thái của các site trên server OMD mới, tránh đặt trùng tên với site đã tồn tại

`omd status`

* Restore lại site
`omd restore news /opt/monitoring-bk.tar.gz`

* Check lại status của site

* Khởi động lại site vừa Restore

` omd start news`

```
[root@cmk-server tmp]# omd start news
Starting mkeventd...OK
Starting rrdcached...OK
Starting npcd...OK
Starting nagios...OK
Starting apache...OK
Initializing Crontab...OK
```

