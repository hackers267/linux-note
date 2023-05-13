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
