+++
title = "设置默认的文件管理器"
date = 2023-08-02
[taxonomies]
tags = ["desktop", "gui", "expoler"]
[extra]
toc = true
+++

# 为linux设置默认的文件管理器

在Linux桌面系统中，文件管理器是一个必不可少的工具，用于浏览，管理和组织文件和文件夹。默认的文件管理器是系统中打开文件和文件夹的首选程序。在本文中，我们将控球如何将PCManFM设置为Linux系统的默认文件管理器。

> 由于在`DE(桌面系统)`中，设置默认的文件管理器通常可以使用GUI完成，比较简单。这里不再详细介绍。

PCManFM是一个轻量级、快速且易于使用的文件管理器，特别适合那步希望保持简单、高效的用户。它是LXDE桌面环境的默认文件管理器，但在其他桌面环境中也可以使用。

## 安装

使用下面的命令来安装`PCManFM`(基于archlinux):

```shell
parc -S pcmanfm-gtk3
```

## 设置为默认文件管理器

安装完成`pcmanfm`后，我们可以通过命令行和配置文件的方式来设置PCManFM为默认文件管理器。

### 使用命令行设置默认文件管理器
```shell
xdg-mime default pcmanfm.desktop inode/directory
```

> 如果没有`xdg-mime`命令，需要安装`xdg-utils`:
```shell
paru -S xdg-utils
```

### 直接通过配置文件修改默认文件管理器

使用`vim ~/.config/mimeapps.list`命令打开`mimeapps.list`文件，找到`inode/directory=`一行，把值修改为`pcmanfm.desktop`,如下所示：

```text
inode/directory=pcmanfm.desktop
```
