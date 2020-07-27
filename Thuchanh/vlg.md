# Cấu hình Giám sát Volume Group và Logical Volume
Như Agent mặc định của checkMK bạn chỉ có thể giám sát một số thông số như **Disk IO SUMMARY**, **Filesystem /**, **Filesystem /boot** mà bạn không thể giám sát IO trên từng Disk vật lý hay IO trên từng Volume

## Thêm giám sát IO trên từng Disk vật lý và Logical Volume

Chọn `Host & Service Parameters` -> `Parameters for discovered services`

![Imgur](https://i.imgur.com/A88gTCk.png)

Tìm `Discovery mode for Disk IO check` -> tạo một Rule:

![Imgur](https://i.imgur.com/a68M9oO.png)

Điền thông tin cho Rule:

![Imgur](https://i.imgur.com/78FX8Wg.png)

Bulk Discovery

![Imgur](https://i.imgur.com/D9JcppX.png)

![Imgur](https://i.imgur.com/DwO9oAT.png)

![Imgur](https://i.imgur.com/BYN0U1D.png)

Finished là OK

Kích hoạt dịch vụ

![Imgur](https://i.imgur.com/wsnNJxN.png)

Kết quả:

![Imgur](https://i.imgur.com/bEMvqF3.png)

