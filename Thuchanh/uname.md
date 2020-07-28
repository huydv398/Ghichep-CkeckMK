# Cài đặt plugin Uname

Đăng nhập CheckMK server để thao tác

Download file mkp

```cd /tmp 
wget https://github.com/HeinleinSupport/check_mk_extensions/raw/master/uname/uname-3.0.mkp
```

Cài đặt Plugin

```
su - [tên_site]

mkp install /tmp/uname-3.0.mkp
```

Sau khi cài xong có thể dùng lệnh để kiểm tra

`mkp list`

Thực hiện copy file uname trong đường dẫn `/opt/omd/sites/cmk/local/share/check_mk/agents/plugins/uname` sang thư mục `/lib/check_mk_agent/plugins/` trên máy client:`10.10.34.115`


```
scp /opt/omd/sites/cmk/local/share/check_mk/agents/plugins/uname root@10.10.34.115:/usr/lib/check_mk_agent/plugins
```
## Đăng nhập vào Web IU để Add Service 

Thực hiện Bulk Discovery 

![Imgur](https://i.imgur.com/4yMs51j.png)

Kích hoạt thay đổi 

Kiểm tra

![Imgur](https://i.imgur.com/9L0sMT4.png)

Link hướng dẫn

https://github.com/niemdinhtrong/thuctapsinh/blob/master/NiemDT/Ghichep_checkmk/docs/09.Event-console.md

https://checkmk.com/cms_mkps.html

