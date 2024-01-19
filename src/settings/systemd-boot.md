# Systemd Boot

systemd-boot，曾用名 gummiboot （德语里“橡皮筏”的意思），是一款可以执行 EFI 镜像文件的简单 UEFI 引导管理器。可以通过配置好的模式（全局）或可用方向键导航的屏幕菜单选择默认条目。Arch 默认安装的 systemd包 包含了 systemd-boot。

## 配置

### 启动选单配置

配置文件保存于 $esp/loader/loader.conf，可指定以下设置：

- default – #增加启动选项 中默认选择的选项，可以使用通配符，例如 arch-*；
- timeout – 启动默认选项前的超时时间（以秒为单位）。如果未设定，选单仅在启动时按空格键（或大多数其他键）显示；
- editor – 是否启用内核参数编辑器。 yes （默认）为启用, no 为禁用；因为用户可以添加 init=/bin/bash 以绕过密码获取 root 权限，如果未经授权的人可以使用这台机器，强烈建议将此选项设置为 no ；
- auto-entries – 自动为 Windows、EFI Shell 和 Default Loader 添加选项， 1 (默认)启用， 0 为禁用；
- auto-firmware – 显示“重启到 UEFI 固件设置”的选项， 1 (默认)启用， 0 为禁用；
- console-mode – 更改 UEFI 控制台模式: 0 为 80x25, 1 为 80x50, 2 and above for non-standard modes provided by the device firmware, if any, auto picks a suitable mode automatically, max for highest available mode, keep (默认) 由固件确定。
- random-seed-mode - 控制是否从文件 $esp/loader/random-seed 中读取随机种子。如果设为 with-system-token （默认），仅在设置了 EFI 变量 LoaderSystemToken 的情况下才从文件加载种子；如果设为 always，即使未设置 EFI 变量，它也会从文件加载种子；如果设为 off 文件将被忽略。


## 启动选单中的按键操作

启动选单中支持的按键操作有:

- Up/Down - 选择选项
- Enter - 加载所选的选项
- d - 设置默认的启动选项 (会保存在 EFI 变量中)
- -/T - 增加超时时间 (会保存在 EFI 变量中)
- +/t - 减少超时时间 (会保存在 EFI 变量中)
- e - 编辑内核参数,如果 editor 选项设置为0,则没有任何作用.
- v - 显示版本信息
- Q - 退出
- P - 显示目前的配置
- h/? - 帮助

这些热键可以在启动管理器时直接指定启动哪一个选项

* l - Linux
* w - Windows
* a - OS X
* s - EFI Shell
* 1-9 -选项的编号
