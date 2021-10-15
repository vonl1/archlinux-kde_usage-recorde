## 用系统iso修复grub
---
### 前因
  本人lenovo r720双系统,然后去win10更新了一下可选驱动,更新了个联想的固件`Lenovo Ltd.-Firmware`,
然后经过重启几次之后,启动时没有grub只剩win10,然后还启动失败,错误代码`inaccessible boot device`
### 排查问题
  经过排查是联想固件更新更改了bios中的设置,影响的有
  - `sata controller mode:ACHI`
  - `secure boot:Disabled`
  - `intel virtual technology:Enabled`<br>
grub文件确实是没见了,等会儿可以使用系统映像修复引导
  
  额外说一下今天下午开vbox发现新建虚拟机里边只有`32bit`,网上一搜是之前`intel virtual technology`没开,开启之后就没这个问题了
### 解决问题
之前u盘用的wepe,现在发现ventoy是真的香,也不用三天两头rufus刷了
1. 软件在u盘上安装完成
2. 去国内的镜像站下载最新的iso,然后拉入u盘,
3. 关机,
4. 开机狂按`F2`进入bios修改上边的三项,`F10`保存退出
5. 按`F12`选择usb
6. 选择`archlinux.iso`,然后等待安装界面
7. 
  ```
  lsblk查看文件磁盘盘符,例如我的
  
  /dev/sda       机械盘
  ***
  
  nvme0n1     259:0    0 465.8G  0 disk 
  ├─nvme0n1p1 259:1    0   200M  0 part /efi
  ├─nvme0n1p2 259:2    0   128G  0 part /
  
  记得根据你自己的磁盘分区改着用
  
  mkdir/mnt/arch    创建挂载点
  mount -t auto /dev/nvme0n1p2 /mnt/arch    挂载系统根目录
  
  arch-chroot /mnt/arch                   进入chroot
  mount -t auto /dev/nvme0n1p1 /efi       挂载引导磁盘
  os-prober                               探测其他系统
  grub-mkconfig > /boot/geub/grub.cfg     生成grubconfig
  grub-install --efi-directory=/efi --target=x86_64-efi /dev/nvme0n1p1      安装grub
  ```
7.重启,此时修复grub完成. 

>参考文章
>https://www.jeremymorgan.com/tutorials/linux/how-to-reinstall-boot-loader-arch-linux/
