# Sử dụng Plugin kiểm tra sự thay đổi file

## Thực hiện trên máy Client Agent:

Download Plugin:

```
cd /usr/lib/check_mk_agent/local

wget https://raw.githubusercontent.com/niemdinhtrong/thuctapsinh/master/NiemDT/Ghichep_checkmk/scripts/check_file_md5.py
# Cấp quyền thực thi cho File
chmod +x check_file_md5.py
```

### Khai báo những file cần kiểm tra
Ở đây, cần xác định được những file cần giám sát sự thay đổi. Mà sự thay đổi của file ảnh hưởng đên sự an toàn của máy. Tùy vào trường hợp mà add file

`vi check_file_md5.py`

Khai báo những file cần kiểm tra vào trong `File = []`

Lưu ý cần khai báo rõ đường dẫn đến file. Ví dụ kiểm tra 2 file `/etc/passwd` và file `/root/.bash_history` thì khai báo như sau:

`FILE = ['/etc/passwd','/root/.bash_history']`

Kiểm tra

`check_mk_agent | grep "File_md5"`


![Imgur](https://i.imgur.com/wrcL4Y9.png)

## Trên Web bulk Discovery 

Tại máy cài Agent chỉnh sửa file.

Cảnh báo được gửi về

![Imgur](https://i.imgur.com/D1v61qr.png)

![Imgur](https://i.imgur.com/ophAFOR.png)

