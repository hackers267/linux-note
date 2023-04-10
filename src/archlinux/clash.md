# Clash

`clash`是一个由`Go`语言开发的多平台代理客户端。

## 安装

```shell
paru -S clash
```

## 配置

首先直接在终端启动clash，然后在`~/.config/clash/config.yaml`中配置一些参数。

```shell
clash
```

Clash启动后会自动下载一个默认的配置文件，并将其保存到`~/.config/clash/config.yaml`中。然后使用自己的配置文件进行配置就行。

## 使用订阅

下载订阅文件
```shell
wget -O config.yaml "订阅地址"
```

## 守护进程

首先要查看`clash`的绝对路径：
```shell
which clash
```

ArchLinux 的默认路径为`/usr/bin/clash`

创建目录并复制文件：
```shell
# 创建文件夹以存储 Clash 相关文件
sudo mkdir -p /etc/clash
# 复制文件
sudo cp ~/.config/clash/config.yaml /etc/clash
sudo cp ~/.config/clash/Country.mmdb /etc/clash
```

创建 systemd 配置文件`/etc/systemd/system/clash.service`:

```shell
sudo vim /etc/systemd/system/clash.service
```

复制以下内容到`clash.service`中:
```textmate
[Unit]
Description=Clash daemon, A rule-based proxy in Go.
After=network.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/bin/clash -d /etc/clash # /usr/bin/clash 为绝对路径，请根据你实际情况修改

[Install]
WantedBy=multi-user.target
```
