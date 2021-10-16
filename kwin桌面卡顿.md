## kwin桌面卡顿
### 个人经历:
- micro-edge-dev-bin画中画出现过画面卡住覆盖在其他页面的上边
- fcitx5输入法输入选项卡住
- youdaodict选词翻译卡住
### 解决办法:
- `kwin_x11 --replace`
- `plasmashell --replace`
- 或者设置快捷键刷新桌面
`设置`->`快捷键`->`自定义快捷键`->`编辑`->`新建-全局快捷键-命令/url`->触发器:`meta+shift+r`->动作:`kwin_11 --replace`
