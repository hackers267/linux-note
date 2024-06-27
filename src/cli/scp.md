# Scp

*scp*（Secure Copy Protocol）命令在Linux和类UNIX系统中用于安全地在本地和远程主机之间复制文件和目录。它基于SSH协议工作，因此提供了加密的数据传输，确保了数据的安全性。下面是使用scp命令的一些基本方法和选项：

## 基本语法：

```Bash
scp [选项] [源文件或目录] [目标地址]
```

## 常用选项：

+ -P port：指定SSH连接的端口号。
+ -r：递归复制整个目录。
+ -C：启用压缩，加快传输速度，特别是在网络延迟较高或带宽较低的情况下。
+ -p：保留原文件的修改时间、访问时间和权限。
+ -q：静默模式，不显示传输进度。
+ -v：详细模式，显示详细的SCP和SSH调试信息。
+ -i identity_file：指定私钥文件路径，用于身份验证。
+ -1：强制使用SSH协议版本1（不推荐，已过时）。
+ -2：强制使用SSH协议版本2（默认）。
+ -4：强制使用IPv4。
+ -6：强制使用IPv6。

## 示例：

### 从本地复制文件到远程主机：

```Bash
scp local_file_path user@remote_host:/remote/path/
```

将本地的local_file_path文件复制到远程主机的/remote/path/目录下。


### 从远程主机复制文件到本地：
```Bash
scp user@remote_host:/remote/path/remote_file local_directory_path/
```

从远程主机的/remote/path/目录下复制remote_file到本地的local_directory_path/目录中。

### 复制目录：


```Bash
scp -r local_directory_path user@remote_host:/remote/path/
```

使用-r选项递归复制本地的local_directory_path目录到远程主机的/remote/path/目录。
