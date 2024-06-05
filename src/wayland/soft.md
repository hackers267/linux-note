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

