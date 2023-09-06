+++
title = "使用firewall-cmd管理防火墙"
date = 2023-09-06

[taxonomies]
tags = ["firewall-cmd","防火墙"]
categories = ["系统管理"]
[extra]
toc = true
+++

在Linux中，防火墙是保护系统安全的重要工具。**firewall-cmd**是CentOS 7及更高版本中Firewalld服务提供的一个命令行工具，用于配置和管理防火墙。本文将介绍如何使用firewall-cmd来管理防火墙。

# firewall-cmd中的基本概念

## 区域

Firewalld是基于区域的防火墙：每个区域都可以配置为授受或拒绝某些服务或端口，因此具有不同的安全级别。区域可以与多个网络接口关联。通常，Firewalld附带一组预配置区域。

# firewall-cmd命令语法

*firewall-cmd*命令的语法如下：

```shell
firewall-cmd <command> [options]
```

其中，选项包括：

- --permanent: 永久生效,不会在重启系统后失效。
- --add-port: 添加端口规则。
- --remove-port: 删除端口规则。
- --add-service: 添加服务规则。
- --remove-service: 删除服务规则。

## 查询防火墙状态

使用以下命令检查防火墙是否启用：

```shell
firewall-cmd --state
```

如果返回*running*，则表示防火墙已启用。如果返回*not running*，则表示防火墙未启用。

## 查看区域信息

我们在上文中已经了解了区域的概念，如果我们想要查看一下有哪些可用区域，可以使用以下命令：

```shell
firewall-cmd --get-zones
```

```
block dmz docker drop external home internal nm-shared public trusted work
```

如果我们想要查看当前应用的区域，可以使用`firewall-cmd --get-active-zones`命令，这个命令会列出当前应用的区域和对应的网络接口。如下：

```
docker
  interfaces: docker0
public
  interfaces: wlan0
```

## 查询防火墙配置

使用以下命令可以查询当前防火墙配置：

```shell
firewall-cmd --list-all
```

这将列出当前的防火墙所有的规则和配置。

如果希望查看指定区域的防火墙的规则和配置，可以使用以下命令：

```shell
firewall-cmd --list-all --zone=<zone_name>
```

其中，<zone_name>是要查询的区域名称。

## 添加和删除端口规则

使用以下命令添加或删除端口规则：

添加端口规则：

```shell
firewall-cmd --add-port=<port_number>/tcp --permanent
```

删除端口规则：

```shell
firewall-cmd --remove-port=<port_number>/tcp --permanent
```

其中，<port_number>是要添加或删除的端口号。使用--permanent选项可以将规则应用到重启后的系统。

# 添加和删除服务规则

使用以下命令添加或删除服务规则：

添加服务规则：

```shell
firewall-cmd --add-service=<service_name> --permanent
```

删除服务规则：

```shell
firewall-cmd --remove-service=<service_name> --permanent
```

其中，<service_name>是要添加或删除的服务名称。使用--permanent选项可以将规则应用到重启后的系统。

# 添加和删除网络接口规则

使用以下命令添加或删除网络接口规则：

添加网络接口规则：

```shell
firewall-cmd --add-interface=<interface_name> --permanent
```

删除网络接口规则：

```shell
firewall-cmd --remove-interface=<interface_name> --permanent
```

其中，<interface_name>是要添加或删除的网络接口名称。使用--permanent选项可以将规则应用到重启后的系统。

# 重新加载防火墙配置

使用以下命令重新加载防火墙配置：

```shell
firewall-cmd --reload
```

这将重新加载防火墙配置文件并使更改生效。

以上是使用firewall-cmd管理防火墙的一些常用命令和操作。通过使用该工具，您可以方便地配置和管理Linux系统的防火墙，提高系统的安全性。
