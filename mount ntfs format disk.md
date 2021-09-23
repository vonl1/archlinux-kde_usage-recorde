## mount ntfs format disk
---
1. you need to install `ntfs-3g`<br> `sudo pacman -S ntfs-3g`
2. after that you need to check out your ntfs disk's uuid,
<br>`lsblk -f`<br>select the disk you want mount,copy the UUID(https://en.wikipedia.org/wiki/Universally_unique_identifier) 
4. for me,i want mount the ntfs disk after start my computer. 
so i edit: `/etc/fstab`,select an editor you prefer like vim nano etc,
in addition edit`/etc/fstab`need you have root permission to save the changes<br>
`sudo vim /etc/fstab`<br>
```
# describe 
UUID=xxxx   mount point     ntfs-3g    defaults 0 0
```
mount point is a folder in your computer,you can select a or creat a new one for mount
>https://wiki.archlinux.org/title/NTFS-3G
