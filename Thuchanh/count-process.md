# Giám sát số lượng proocess của dịch vụ

Trong bài lab sẽ thực hiện đếm số Process của dịch vụ.

* Kiểm tra các Process của dịch vụ

`[root@srv-c7 ~]# ps -ef | grep sshd`

Kết quả 
```
[root@srv-c7 ~]# ps -ef | grep sshd
root       985     1  0 13:43 ?        00:00:00 /usr/sbin/sshd -D
root      1031   985  0 13:43 ?        00:00:00 sshd: root@pts/0
root      1455   985  0 13:43 ?        00:00:00 sshd: root@notty
root     14488   985  0 15:16 ?        00:00:00 sshd: root@pts/1
root     14611   985  0 15:16 ?        00:00:00 sshd: root@notty
root     14635   985  0 15:17 ?        00:00:00 sshd: root@pts/3
root     14637   985  0 15:17 ?        00:00:00 sshd: root@pts/2
root     14639   985  0 15:17 ?        00:00:00 sshd: root@notty
root     14661   985  0 15:17 ?        00:00:00 sshd: root@notty
root     17576  1457  0 15:40 pts/0    00:00:00 grep --color=auto sshd

```

Sử dụng câu lệnh sau để tiến hành đếm số lượng hiện có với dụ HTTP:

` pidof sshd | wc -w`

kết quả

```
[root@srv-c7 ~]# pidof sshd | wc -w
9
```

* Như vậy kết quả cho thấy dịch vụ sshd đang có 9 process trên hệ thống.

Bây giờ chúng ta tiến hành giám sát các tiến trình dịch vụ sshd. 

## Tiến hành giám sát

Tại **WATO** chọn `Manual checks` -> tìm `State and count of processes`

![Imgur](https://i.imgur.com/yIvRWfY.png)

Tạo một rule mới

![Imgur](https://i.imgur.com/tBECXVr.png)

Điền thông tin cho rules

![Imgur](https://i.imgur.com/fUZ9Tos.png)

Điền thông số như sau:

![Imgur](https://i.imgur.com/JotVxnj.png)

Lưu lại 

Thay đổi và kích hoạt

![Imgur](https://i.imgur.com/TzPJ8DE.png)

![Imgur](https://i.imgur.com/d7vEpBM.png)