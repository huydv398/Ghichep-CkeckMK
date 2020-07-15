# Các bước cài đặt CheckMK Server 
Mục lục

1. [Triển khai mô hình]()
2. []()
3. []()
4. []()

## 1.Mô hình triển khai

Tạo một máy chủ CentOS-7 làm Check_MK Server 
## 2.IPPlanning
![Imgur](https://i.imgur.com/2fbMS38.png)
## 3. Thiết lập ban đầu

#### Cài đặt các gói cần thiết

`yum install -y epel-release wget`

#### Download file cài đặt

Tải file cài đặt:

`wget https://checkmk.com/support/1.6.0p10/check-mk-raw-1.6.0p10-el7-38.x86_64.rpm`

Cài đặt CheckMK

`yum install -y check-mk-raw-1.6.0p10-el7-38.x86_64.rpm`

Tạo một site 

`omd create cmk`

Khởi động site

`omd start cmk`

Đổi mật khẩu cho User **cmkadmin**

```
su - cmk
htpasswd -m etc/htpasswd cmkadmin

#Nhập mật khẩu cho user
New password:
Re-type new password:
Updating password for user cmkadmin

```

Quay lại User **root** để thực hiện tiếp câu lệnh (`Ctrl` + `d`)

Mở Port cho Http

```
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload
```

Tắt SELinux

```
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
setenforce 0
```

Truy cập bằng trình duyệt và nhập địa chỉ như sau:

`http://10.10.34.114/huycheck` và sử dụng user cmkadmin và password bạn đặt bên trên để đăng nhập.

![Imgur](https://i.imgur.com/Mt6rh0X.png) 

Giao diện chính của CheckMK

![Imgur](https://i.imgur.com/ITW0RBw.png)

