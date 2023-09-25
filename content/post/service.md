+++
title = "自定义linux服务"
date = 2023-09-25
[taxonomies]
tags = ["系统"]
[extro]
toc = true
+++

# 自定义Linux服务

我们知道，当我们需要在Linux管理我们的程序的时候，我们往往需要使用到大量的命令或者很多的手工操作。有时候为了可以避免这些手工操作，我们就需要通过自
服务的方式来处理。

## 什么是Linux服务

Linux服务和window中的任务有着相似的概念。通过使用Linux服务，我们就可以使用`systemctl`命令来对Linux的的程序进行启动，关闭或是重启，甚至可以设置开机启动。Linux服务为我们管理程序提供了很多的方便。

## 服务文件

Linux中的服务文件是一个以`xxx.service`命令的文件。通过编写`xxx.service`文件和`systemctl`就可以实现对linux服务的管理。我们可以查看linux的`/usr/lib/systemd/system/`目录。下面有很多系统或是在安装了软件或程序后生成的服务文件。linux的服务文件的包括很多要学习的内容，今天这里先学习比较基础的部分：
`[Unit]`,`[Service]`和`[Install]`。

基础结构如下：

```
[Unit]
Description=服务描述
After=服务依赖

[Service]
Type=服务类型
ExecStart=启动命令
ExecStop=终止命令
ExecReload=重启命令

[Install]
WantedBy=服务安装设置
```

### Unit

`Unit`部分是一个服务文件中的基础部分。其主要作用是对服务的一些描述和启动顺序等。

Unit中的Description字段给出的是在服务的描述信息，主要是为了可以在启动后知道服务的作用。而`Before`和`After`字段给出了服务的启动顺序。即在该服务启动前后要启动哪些服务。

### Service

`Service`是服务的核心部分，其主要是定义了服务的各个命令的作用，如`ExecStart`定义的是`systemctl start`命令的作用，通过自定义各个字段，我们可以自由的响应`systemctl`的命令

### Install

Install命令中的WantedBy命令用于定义如何安装这个配置文件，即怎样做到开机启动。

## 各种服务的示例

### 自定义rust的web服务

```
[Unit]
Description=rust的web服务

[Service]
Type=forking
WorkingDirectory=/usr/local/web/xxx
ExecStart=/usr/local/web/xxx/web
[Install]
WantedBy=multi-user.target
```

配置文件中的`WorkingDirectory`字段用于配置命令当前的工作目录，以解决在启动命令后程序中使用相对路径的问题。
