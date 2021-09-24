## 挂载ntfs磁盘
---
1. `sudo pacman -S ntfs-3g`
2.  `lsblk -f`记录下需要挂载的ntfs磁盘UUID
3.  创建一个空的文件夹以供挂载使用,并记下文件夹目录
4. `sudo vim /etc/fstab'
```
# xxxx是你刚才复制的UUID 磁盘格式是ntfs-3g不要填成ntfs
UUID=xxxx   挂载的文件夹目录     ntfs-3g    defaults 0 0
```
>https://wiki.archlinux.org/title/NTFS-3G

### 常见问题:
- win10关机不正常,导致linux下挂载的磁盘无法正常写入,建议关闭`win10/电源键选项`里边的快速启动
- UUID错误,导致桌面启动时失败,进入命令行终端中修改`/etc/fstab`
