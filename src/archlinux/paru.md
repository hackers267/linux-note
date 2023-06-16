# Paru

`Paru`是ArchLinux下`Pacman`的一个安装包包装器。使用`Paru`可以帮助我们更好的在`ArchLinux`中管理安装包。

## 安装

想要安装`paru`，只要使用下面的命令安装即可。
```shell
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```
当使用了上面的命令后，我们已经安装好了`paru`了。

## 使用

在我们安装了`paru`后，我们就可以使用`paru`来安装`archlinux`软件了。

下面常使用的一部分命名：

- *paru* 同步源，并更新系统(同`paru -Syu`)
- *paru -Sy* 仅同步源
- *paru -Sua* 更新当前安装的所有Aur包
- *paru -Ss foo* 搜索*foo*包
- *paru -Si foo* 获取*foo*包的信息
- *paru foo* 交互式安装*abc*包
- *paru -c* 删除没有依赖的包
- *paru -Qs* 显示本机的已经安装的包
- *paru -Qs foo* 显示本机中已经安装的包中有*foo*有关的包
- *paru -Scc*  删除本地没有`git`控制的缓存包(以交互方式)
- *paru -Sccd*  删除本地所有的缓存包(以交互方式)
- *paru -Rns foo* 删除指定的包和其没有必要的依赖
- *paru -Qdt* 列出不再其他包作为依赖的包 
- *paru -Qm* 列出已安装的独立包