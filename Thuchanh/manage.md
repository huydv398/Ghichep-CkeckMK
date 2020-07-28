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

Tạo một site mới