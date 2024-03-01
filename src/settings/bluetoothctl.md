# 蓝牙设置

要在 *Linux* 中使用蓝牙,可以使用 *bluetoothctl* 命令行工具。

## 安装 *bluetoothctl* 

在 *ArchLinux* 中，可以使用 `pacman` 或 `paru` 来安装　*bluetoothctl*。

```
  paru -S bluez-utils
```


## 交互命令

- 搜索蓝牙 `scan on`
- 停止搜索蓝牙 `scan off`
- 配对 `pair [dev]`
- 连接 `connect [dev]`


