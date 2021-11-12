### 前景提要

---

之前网上看到nvidia支持wayland了,然后过段时间又看到[nvidia开发者社区的教程](https://forums.developer.nvidia.com/t/nvidia-495-on-sway-tutorial-questions-arch-based-distros/192212):arch+wayland+sway+nvidia,刚好自己之前也用过i3wm,现在用着arch+kde,所以就试一试(就是折腾),参考着上边的例子,上午折腾了起来.

### 折腾的过程

---

先进tty2,安装上sway,然后启动sway,输入`sway --my-next-gpu-wont-be-nvidia`回车,先进去看看,这时候切tty1是kde,tty2是sway,看着kde里的教程开始操作

1. 基本要求:基于arch的发行版+nvidia独显,下边是我根据下边的评论中有用的设置:wayland相关的系统变量设置

```shell
sudo vim /etc/environment

CLUTTER_BACKEND=wayland
SDL_VIDEODRIVER=wayland
XDG_SESSION_TYPE=wayland
QT_QPA_PLATFORM=wayland
QT_WAYLAND_DISABLE_WINDOWDECORATION=1
MOZ_ENABLE_WAYLAND=1
GBM_BACKEND=nvidia-drm
__GLX_VENDOR_LIBRARY_NAME=nvidia
WLR_NO_HARDWARE_CURSORS=1
```

2. 先去[Frogging-Family/nvidia-all](https://github.com/Frogging-Family/nvidia-all)这里查看怎么安装

```shell
git clone https://github.com/Frogging-Family/nvidia-all.git
cd nvidia-all
makepkg -si
```

3. 从AUR安装`libxcb-git`
4. 从AUR安装`mesa-git`
5. 从AUR安装`lib32-libglvnd-git`和`libglvnd-git`
6. 从AUR安装`egl-wayland-git`
7. 从AUR安装`xorg-wayland-git`
8. 从AUR安装`libdrm-git`
9. 编辑`/etc/mkinitcpio.conf`以便于我们尽快使用nvidia驱动`MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)`,然后更新一下`sudo mkinitcpio -P`
10. 编辑`/etc/default/grub`添加`GRUB_CMDLINE_LINUX_DEFAULT='rd.driver.blacklist=nouveau nvidia-drm.modeset=1'`,然后更新grub`sudo grub-mkconfig -o /boot/grub/grub.cfg`
11. 这时可以测试一下`nvidia-smi`,查看输出信息
12. 从AUR安装`wlroots-git`和`sway-git`,这里就是发生玄学的地方,git版本不行的换成`wlroots`和`sway`,tty启动输入`sway --my-next-gpu-wont-be-nvidia
13. 教程这里是重启后启动sway,然后测试`nvidia-sim`,看是否使用nvidia独显
14. 从AUR安装`vulkan-tools`,命令行运行`vkcube`进行测试
15. 如果有问题请排查`9,10,12`步

### 使用感受

---

- microsoft-edge-dev看archwiki过程中页面滑动出现果冻屏感觉
- edge在打开其他页面过程中屏幕出现白线闪烁,reddit上swaywm上有[同样问题](https://www.reddit.com/r/swaywm/comments/qnlusa/white_artifacts_with_nvidia_driver_49544/)
- 按照nvidia开发者论坛的教程中间会有比较玄学的问题,作者-git版本的软件教程成功了,然后我自己跟着试失败了,根据下边的回复换成非git版本的就又成功了
- nvidia is in used,中间没有记录怎么搞定的
- 安装过程中把xorg+kde的包给删了,**记得不要`Rsc`不看就删了**,`Rs`慢慢看着包操作
- 使用体验感觉还不如xorg+kde,然后我又切回xorg+kde了,中间手机拍的![图片](http://images.vonlee.cn/PXL_20211111_033849277.jpg)

### 总结

---

**wayland+sway+nvidia不太行,至少现在不太行**

wayland+gnome没有尝试

wayland+kde也不会尝试了

心静了现在,kde养老,以后有时间再折腾折腾i3
