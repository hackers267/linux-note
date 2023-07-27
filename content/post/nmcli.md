+++
title = "使用nmcli管理网络"
date = 2023-07-27

[taxonomies]
tags = ["network", "cli"]
[extra]
toc = true
+++

# 使用nmcli管理网络

## 介绍

在现代社会中，网络连接已经感染我们睡觉生活中不可或缺的一部分。无论是家庭网络，还是在工作场所或公共场所使用Wi-Fi,我们都需要一种简单而高效的方式来管理和配置这些网络连接。在Linux操作系统中，nmcli是一个功能强大的命令行工具，它可以帮助我们轻松地管理连接。本文将向您介绍如何使用nmcli来配置和管理网络连接。

## 什么是nmcli

nmcli是NetworkManager命令行客户端，它是NetworkManager工具套件的一部分。

NetworkManager是一种在大多数Linux发行版中广泛使用的网络连接管理器。nmcli允许用户通过命令行与NetworkManager进行交互，从而配置、管理和监视网络连接。

## 检查nmcli是否安装

在开始使用nmcli之前，首先需要确保nmcli已经安装在您的Linux系统中。大多数Linux发行版默认安装了NetworkManager和nmcli，但如果您不确定是否已安装，请打开终端并输入以下命令：

```bash
nmcli --version
```

如果您看到输出信息显示版本号等相关内容，则nmcli已经安装在您的系统中。如果没有安装，可以使用适用于您的Linux发行版的包管理器进行安装。

## 查询操作

### 1.查看网络状态

要查看当前网络连接状态，可以运行以下命令:

```bash
nmcli connection show --active
```

这会列出现在连接的网络连接。

如果您想查看所有网络连接状态，可以运行以下命令:

```bash
nmcli connection show
```

这将显示所有已定义的网络连接的名称、类型、设置等信息。

### 2.连接到Wi-Fi网络

如果您的系统支持Wi-Fi功能，并且附近有可用的Wi-Fi网络，您可以使用以下命令连接到Wi-Fi网络

```bash
nmcli device wifi list
```

这个命令会列出附近可用的Wi-Fi网络及其相关信息，例如SSID、信号强度等。然后，选择要连接的Wi-Fi网络并运行以下命令：

```bash
nmcli device wifi connect <SSID> password <PASSWORD>
```

请将"<SSID>"替换为您想要连接的Wi-Fi网络的名称，并将"<PASSWORD>"替换为您想要连接的Wi-Fi网络的密码。如果连接成功，您的系统将会连接到该Wi-Fi网络。

### 3.切换网络

如果您想在多个网络之间切换，可以使用以下命令:

```bash
nmcli connection up <SSID>
```

### 4.断开连接

如果您想断开连接，可以使用以下命令:

```bash
nmcli connection down <SSID>
```

### 5.删除连接

如果您想删除连接，可以使用以下命令:

```bash
nmcli connection delete <SSID>
```

## 总结

nmcli是一个非常强大且灵活的命令行工具，它可以帮助我们轻松地管理和配置网络连接。在本文中，我们介绍了一些基本操作，例如查看网络状态、连接到Wi-Fi网络、创建有线连接、断开连接和删除连接。使用这些命令，您可以轻松地配置和管理您的网络连接，为您的Linux系统提供更好的网络体验。

无论您是Linux新手还是有经验的用户，nmcli都是一个值得掌握的工具。希望本文能够帮助您更好地理解和使用nmcli，并在日常使用中提升您的效率。祝您网络畅通，愉快上网！
