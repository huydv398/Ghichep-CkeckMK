# Quản lý site trên OMD

https://github.com/datkk06/meditech-ghichep-omd/blob/master/docs/10.2.Backup-site-use-CMD.md

## Giới thiệu 
OMD sử dụng câu lệnh `omd [option]`. Trong đó có các Option như sau:

```
[root@cmk-server tmp]# omd help
Usage (called as root):

 omd help                               Show general help
 omd setversion VERSION                 Sets the default version of OMD which will be used by new                                                                                         sites
 omd version    [SITE]                  Show version of OMD
 omd versions                           List installed OMD versions
 omd sites                              Show list of sites
 omd create     SITE                    Create a new site (-u UID, -g GID)
 omd init       SITE                    Populate site directory with default files and enable the                                                                                         site
 omd rm         SITE                    Remove a site (and its data)
 omd disable    SITE                    Disable a site (stop it, unmount tmpfs, remove Apache hoo                                                                                        k)
 omd enable     SITE                    Enable a site (reenable a formerly disabled site)
 omd mv         SITE NEWNAME            Rename a site
 omd cp         SITE NEWNAME            Make a copy of a site
 omd update     SITE                    Update site to other version of OMD
 omd start      [SITE] [SERVICE]        Start services of one or all sites
 omd stop       [SITE] [SERVICE]        Stop services of site(s)
 omd restart    [SITE] [SERVICE]        Restart services of site(s)
 omd reload     [SITE] [SERVICE]        Reload services of site(s)
 omd status     [SITE] [SERVICE]        Show status of services of site(s)
 omd config     SITE ...                Show and set site configuration parameters
 omd diff       SITE ([RELBASE])        Shows differences compared to the original version files
 omd su         SITE                    Run a shell as a site-user
 omd umount     [SITE]                  Umount ramdisk volumes of site(s)
 omd backup     SITE [SITE] [-|ARCHIVE_PATH] Create a backup tarball of a site, writing it to a f                                                                                        ile or stdout
 omd restore    [SITE] [-|ARCHIVE_PATH] Restores the backup of a site to an existing site or crea                                                                                        tes a new site
 omd cleanup                            Uninstall all Check_MK versions that are not used by any                                                                                         site.


```

## Tạo một site mới

Trước khi sử dụng được CheckMK thì cần phải tạo một site Web UI

`omd create [tên_site]`

[Imgur](https://i.imgur.com/5eFqChN.png)

Như vậy một site có tên là: site đã được tạo ra và phần thông tin trong hình. Mặc định, Username được cấp là **cmkadmin** và Password: **PD5H74Wf**

## Cấu hình site

`omd config site`

![Imgur](https://i.imgur.com/b1p1Vzv.png)

* `Basic`: Cấu hình Core của OMD

![Imgur](https://i.imgur.com/XWVlxsj.png)

* `Web UI`: Cấu hình Web UI

![Imgur](https://i.imgur.com/O6QEzBh.png)

* `Addons`: Cấu hình các Addon

!https://i.imgur.com/ML3uJMS.png

* `Distributed Monitoring`: Cấu hình giám sát tập chung

![Imgur](https://i.imgur.com/gmwS5s5.png)

## Khởi động site

`omd start site`    

Truy cập Web UI bằng :

`http:Địa_chỉ_ip/site`

Giao diện sau khi đăng nhập:

![Imgur](https://i.imgur.com/KzCdEwq.png)

## Đổi mật khẩu cho `cmkadmin`

để đảm bảo tính an toàn bảo mật, chúng ta thay đổi user và password cho **site**

![Imgur](https://i.imgur.com/AH72ywC.png)

Nhập thông tin mới Password cho user **cmkadmin**

![Imgur](https://i.imgur.com/gjRkTyu.png)

Sau đó **Save**

## Dừng hoạt động của site

`omd stop site`

## Xóa site
`omd rm site`
