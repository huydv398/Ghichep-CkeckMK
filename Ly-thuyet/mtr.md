# Lệnh mtr- Một công cụ chuẩn đoán mạng

mtr - my traceroute là một công cụ chuẩn đoán mạng mạnh mẽ cung cấp chức năng 2 lệnh ping và traceroute. Nó là một công cụ đơn giản và đa nền tảng in thông tin về toàn bộ tuyến đường mà các gói mạng thực hiện ( giống traceroute). Tuy nhiên, lệnh mtr cho nhiều thông tin hơn traceroute: nó xác định đường dẫn đến một máy tính từ xa trong khi in phần trăm phản hồi cũng như thời gian phản hồi của tất cả các bước nhảy mạng trong tuyến internet giữa hệ thống cục bộ và máy từ xa.

## Cách mtr hoạt động

Khi bạn chạy `mtr`, nó sẽ kết nối mạng giữa hệ thống cục bộ và máy chủ từ xa mà bạn đã chỉ định đầu tiên, nó thiết lập địa chỉ của từng mạng ( cầu nối, bộ định tuyến và cổng, v.v) giữa các máy chủ, sau đó ping(gửi một chuỗi yêu cầu ICMP tới) để xác định chaatgs lượng của liên kết đến từng máy.

Trong quá trình hoạt động này, mtr đưa ra một số thống kê hữu ích về mỗi máy - được cập nhật theo thời gian thực theo mặc định.

## Cài đặt

* Debian & Ubuntu

```
apt update && apt upgrade
apt install mtr-tiny
```
* CentOS/RHEL

`yum install update`

`yum install mtr`

## Sử dụng hướng dẫn sử dụng

Kiểm tra kết nối tới IP/domain

`mtr [IP/domain]`

Ví dụ:

