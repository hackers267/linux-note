# 常见问题

### 如何使用命令行打开`firefox`的隐私模式?

```
firefox --private-window https://www.baidu.com/
``` 

### 如何查看已安装字体？

在`linux`中，如果有查看已安装字体的需要，可以使用`fc-list`命令，如果需要查看的是中文字体，可以使用`:lang=ZH`参数。

比如：
```shell
fc-list :lang=ZH
```

如果你是在`nushell`终端下，还可以使用下面的命令来获取更好的可视化效果：

```nushell
fc-list :lang=ZH | lines | split column ':' location name
```

## 挂载硬盘

当计算机中不止一块硬盘的时候，可以通过挂载助手 *udisks2* 来挂载硬盘。

使用方式很简单：

挂载 `udisksctl mount /dev/sdb1`

卸载 `udisksctl unmount /dev/sdb1`

有一个问题是，当我们挂载硬盘的时候， *udisks2* 会默认把硬盘挂载到 */run/media/$USER/* 目录下，有时候其名称会是一个 莫名其妙 的字符串。其实这个时候， *udisks2* 使用的是硬盘分区的 *IdUUID* 作为名称的，其硬盘分区的 *IdLabel* 为空，具体信息可以使用 *udisksctl info -b /dev/sdb1* 查看，为了使挂载后的名称有意义，我们可以为 */dev/sdb1* 设置一个 *IdLabel* 。

### 设置 IdLabel

#### ext* 分区

如果你的分区是 *ext2*, *ext3* 或 *ext4* ,可以使用 *e2label* 工具修改

```shell
e2label /dev/sdb1 <IdLabel>
```

 修改完成后，就可以以 *IdLabel* 挂载硬盘了。

#### ntfs 分区

如果你的分区是 *ntfs* ，可以使用 *ntfslabel* .

```shell
ntfslabel /dev/sdb1 <name>
```

#### exfat 分区

```shell
exfatlabel /dev/sdb1 <name>
```

#### swap 分区

```shell
mkswal -L <name> /dev/sdb1
```
