+++
title = "如何在Arch Linux中降级软件包"
descriptions = "如何在Arch Linux中降级软件包"
date = 2023-09-08
[taxonomies]
tags = ["archlinux"]
categories = ["软件"]
[extra]
toc = true
+++

# 如何在Arch Linux中降级软件包

如我们所知，`Arch Linux`是一个滚动发行版本，其中的软件每天都会更新。当在更新软件后，难免会出现更新后的软件出现一些问题，为了系统的稳定性和可用性，有时候，我们就需要通过一下的方法来回滚或降级软件。

## 在Arch Linux中降级一个软件

众所周知，我们可以通过`pacman`或`paru`来更新我们的系统和软件。但是直接通过`pacman`或`paru`来降级软件却不是一个很好的选择。其降级软件比较繁琐。在这里，推荐使用一个叫`downgrade`的包来完成软件的降级。

## 安装`downgrade`

在Arch Linux的官方仓库中，并没有`downgrade`，如果想通过安装助手来安装`downgrade`，那么就需要添加非官方的仓库`archlinuxxfr`或`archlinuxcn`。这里以添加`archlinuxcn`为例。

### 添加`archlinuxcn`仓库

要在Arch Linux中添加`archlinuxcn`仓库，请打开并编辑文件`/etc/pacman.conf`:

```shell
sudo vim /etc/pacman.conf
```

在文件中添加如下内容：

```shell
[archlinuxcn]
SigLevel = Never
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```

保存并关闭文件。

### 安装`downgrade`

> 注：本文中使用`paru`作为安装助手，而不是`pacman`,如果你使用`pacman`，那么就查看`pacman`对应的使用方法。

在添加完`archlinuxcn`后，我们首先需要先更新仓库：

```shell
paru -Sy
```

在更新完仓库后，我们就可以使用`paru`来安装`downgrade`了。

```shell
paru -S downgrade
```

## 使用`downgrade`降级软件

在安装完`downgrade`后，我们就可以使用`downgrade`来降级软件了。

使用方法如下，这里以`freetype2`为例：

```shell
sudo downgrade freetype2
```

```
1) freetype2 2.10.0 1 远端
2) freetype2 2.10.0 2 远端
3) freetype2 2.10.1 1 远端
4) freetype2 2.10.1 2 远端
5) freetype2 2.10.2 1 远端
6) freetype2 2.10.3 1 远端
7) freetype2 2.10.4 1 远端
8) freetype2 2.10.0 1 远端
...
19) freetype2 2.13.1 1 远端
20) freetype2 2.13.2 1 远端
21) freetype2 2.13.2 1 /var/cache/pacman/pkg
```

只要使用键盘选择你要降级的软件或输入要降级的软件的编号，然后按回车就可以安装了。

在安装完成后，我们就完成了软件的降级。

> 注意：在安装软件后，`downgrade`会寻问你是否需要把降级的软件加入到`IgnorePkg`中，如果选择是，那后期升级软件中，这个软件会被忽略。如果选择否，在后期的升级软件中，这个软件依然会升级。

## 总结

在使用Arch Linux中过程中，我们需要使用的软件可能并不是最新的或需要降级软件的需求。在这个时候，`downgrade`包可以方便的为我们提供旧软件的安装和软件的降级。
