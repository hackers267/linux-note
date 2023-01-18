# 触摸板

## 开机启动轻触点击和自然滚动

在`/etc/X11/xorg.conf.d/`中创建`70-touchpad-settsings.conf`文件，然后添加如下的代码：
```
Section "InputClass"
    Identifier "deviceName"
    MatchIsTouchpad "on"
    Option "Tapping" "on"
    Option "NaturalScrolling" "on"
EndSection
```

## 使用命令行临时启用

> 下面使用到的`$touchpad`可以使用touchpad的设备名称，也可以使用设备id，得要注意的是，设置id在每次设置重启后，有可能会改变。

临时启用轻触点击：
```
xinput set-prop "$touchpad" "libinput Tapping Enabled" 1
```

临时启用自然滚动：
```
xinput set-prop "$touchpad" "libinput Natural Scrolling Enabled" 1
```
