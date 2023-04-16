# ArchLinux

`ArchLinux`是Linux系统的一个个性化定制很强的操作系统。你可以最大程度的定制自己的操作系统。它可以让你尽早的体验Linux系统中的新功能。

## Paru

[paru](./paru.md)是ArchLinux中新出的一个包安装器，其基于*Rust*语言。可以帮助我们更好的安装和管理软件。

### 常用命令

- `paru -Qi zsh` 查看本地安装的`zsh`的相关信息，其中包括其依赖的包，被其依赖的包，可选依赖包等。
- `paru -Si zhs` 查看仓库中包`zsh`的相关信息，其中包括其依赖的包，被其依赖的包，可选依赖包等。
- `paru` 同`paru -Syu` 同步库，并更新本地的软件到最新版本 
- `paru -Rc zsh` 卸载并清理`zsh`
- `paru zsh` 搜索并安装`zsh`

## clash

[clash](./clash.md)是使用`Go`语言实现的一个多平台代理客户端。

目前`clash`是其核心实现，并没有UI界面。

## rofi

[rofi](./rofi.md)是一个命令行的启动器。

命令行启动器

## screenkey

[screenkey](./screenkey.md)是linux中的一个键盘操作记录器。

## polybar

[polybar](./polybar.md)是一个linux中的自定义状态栏工具。
