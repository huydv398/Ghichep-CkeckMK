# Cài đặt thêm Iventory phần cứng giám sát server vật lý

https://github.com/domanhduy/ghichep/blob/master/DuyDM/Check-MK/thuc-hanh/docs/6.add-monitor-inventory-hardware-checkmk.md

https://github.com/datkk06/meditech-ghichep-omd/blob/master/prepare/3.Inventory.md

Ngữ cảnh sử dụng: Server vật lý

Các bước thực hiện

Trên Wato Chọn `Host & Service Parameters` -> `Harware/Software-inventory`:

![Imgur](https://i.imgur.com/hq1gjyK.png)

Chọn `Do hardware/software Inventory`

![Imgur](https://i.imgur.com/k2KrCo8.png)

Create Rule

![Imgur](https://i.imgur.com/68MAmMl.png)

Điền đầy đủ thông tin:

![Imgur](https://i.imgur.com/6aF9jwG.png)

sau đó lưu lại


Copy plugin từ CheckMK server 

**Cách một copy từ CheckMK WEB UI**

Sao chép địa chỉ liên kết:

![Imgur](https://i.imgur.com/WBybf5L.png)

Tải về máy cần giám sát hardware 

![Imgur](https://i.imgur.com/MSBmH6H.png)

```
cd /usr/lib/check_mk_agent/local/
wget https://checkmk.duonghuy.xyz/check_mk/agents/plugins/mk_inventory.linux
chmod +x mk_inventory.linux

#kiểm thử
./mk_inventory.linux
```
**Cách hai: copyfile** 

`scp /opt/omd/versions/1.6.0p14.cre/share/check_mk/agents/plugins/mk_inventory.linux root@[ip_may_giamsat]:/usr/lib/check_mk_agent/local/`

Tại Web ui check lại Inventory

![Imgur](https://i.imgur.com/4qKf1vS.png)

![Imgur](https://i.imgur.com/ehvbK4h.png)
