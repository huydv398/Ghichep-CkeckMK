# Cài đặt agent của Check_MK trên CentOS-7

## Mô hình 
Mô hình vật lý

![Imgur](https://i.imgur.com/nJ48UCR.png)

IPplanning:

![Imgur](https://i.imgur.com/r8xm6nh.png)

## Các bước thực hiện với máy Client CentOS-7

### Tìm agent phù hợp cho máy Client

Tại máy Check_MK server tìm agent phù hợp cho CentOS-7. Bản Agent phù hợp với CentOS-7 phải có đuôi file là `.rpm`

Kéo Menu tìm TAB `WATO - CONFIGURATION` -> Chọn Monitoring Agents

Tìm Agent phù hợp:

![Imgur](https://i.imgur.com/saJxWGH.png)

Sao chép liên kết download, Ví dụ agent có Link như sau: `http://10.10.34.114/cmk/check_mk/agents/check-mk-agent-1.6.0p10-1.noarch.rpm`

Trên các Website của Check_MK Server khi bạn cài đặt thành công và đăng nhập vào nó sẽ hỗ trợ và hiển thị cho bạn 3 loại agent. Việc của bạn là chọn Agent phù hợp với hệ điều hành của mình. Ở đây tôi cài đặt Agent trên CentOS-7 nên tôi sẽ chọn agent có đuôi là .rpm

>**Lưu ý**: Các bưới dưới đây tất cả đều phải thực hiện trên máy Client mà bạn muốn được giám sát. và các Command line được chạy dưới quyền User sudo hoặc User root

#### Cài đặt gói wget

`yum install -y wget` 

* wget là package dùng để tải package bằng link download về máy

Dùng gói wget doownload agent đã cọn ở bước trên 

`wget http://10.10.34.114/cmk/check_mk/agents/check-mk-agent-1.6.0p10-1.noarch.rpm`

Cấp quyền thực thi cho file vừa download 

`chmod +x check-mk-agent-1.6.0p10-1.noarch.rpm`

Cài đặt agent

`rpm -ivh check-mk-agent-1.6.0p10-1.noarch.rpm`

Cài đặt xinetd

`yum install xinetd -y`

Khởi động xinetd

```
systemctl start xinetd
systemctl enable xinetd
```

Cài đặt net-tools để kiểm tra các Port trên Client

`yum install -y net-tools`

Mở port trên client để có thể giao tiếp với Check_MK sẻver

`vi /etc/xinetd.d/check_mk`

Sửa các thông số sau:

```
only_from      = 10.10.34.114
disable        = 0
port           = 6556
```

Kiểm tra port mặc định của Check_MK sử dụng để giám sát được chưa

```
# netstat -npl | grep 6556
tcp6       0      0 :::6556                 :::*                    LISTEN      1/systemd`
```

Mở port trên firewall 

```
 firewall-cmd --add-port=6556/tcp --permanent
 firewall-cmd --reload
```

Tắt SELinux

`setenforce 0`

