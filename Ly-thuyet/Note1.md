# Note

Khi đứng ở bảng điều khiển thực hiện test gặp lỗi như sau:

![Imgur](https://i.imgur.com/UEmdnhX.png)

Thực hiện :
* list package check-mk: `rpm -qa | grep check-mk`
* dùng `rpm -e [package-checkmk]`
* Cài đặt lại packege : `rpm -ivh [check-mk Agent]`
* Sửa lại file `xinetd`
* Restart xinetd

Thực hiện test lại.
