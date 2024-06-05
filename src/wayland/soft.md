# 软件

在`wayland`中，已经有不少软件的支持了，下面是可以使用的一个列表:

- 窗口管理器
  - sway
  - hyprland
- 输入法
  - fcitx5
- 终端模拟器
  - alacritty
  - kitty
- 浏览器
  - firefox
  - vavildi(需要配置)
- 图片查看器
  - imv
- 文件管理器
  - pcmanfm
- 启动器
  - rofi-lbonn-wayland-git
- 截图软件
  - grim + slurp
- 剪切板管理
  - wl-clipboard 剪切板
  - cliphist 剪切板管理工具

## wayland下vavildi的设置

在默认情况下，vavildi在wayland中是运行在 *xwayland* 模式下的，如果我们需要其运行在 *wayland* 模式下，就需要设置[ozone](vivaldi://flags/#ozone-platform-hint)选项为`auto`。这样，vavildi就直接运行在 *wayland*模式下了，但是，在这个时候输入法是不能使用的，如果要让输入法可用，需要在启动时使用`--enable-wayland-ime`选项。

## 剪切板管理

在`wayland`中，可以使用`wl-clipboard`对系统剪切板进行基本的管理操作。`wl-clipboard`工具包含两个基本的命令行命令:`wl-copy`和`wl-paste`,其中一个用于复制，同时另一个用于粘贴。其基本使用如下:

```shell
# 复制简单的文本:
$ wl-copy Hello world!

# 复制*~/Downloads*中的目录文件:
$ ls ~/Downloads | wl-copy

# 复制图片:
$ wl-copy < ~/Pictures/photo.png

# 复制前一个命令:
$ wl-copy "!!"

# 粘贴到文件:
$ wl-paste > clipboard.txt

# 排序剪贴板中的内容:
$ wl-paste | sort | wl-copy

# Upload clipboard contents to a pastebin on each change:
$ wl-paste --watch nc paste.example.org 5555
```
