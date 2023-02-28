# Zoxide

`zoxide`是一个更加现代化的`cd`命令的替代品。它可以记录你频繁访问的目录，然后通过命令可以快速跳转到常访问的目录之中，比`cd`命令更加快捷。

![`zoxide`的基本使用](../../assets/tutorial.webp "示例")

## 命令行的使用

```shell
z foo # 进入和`foo`匹配度最高的目录中
z foo bar # 进入和*foo*和*bar*匹配度最高的目录
z foo / # 进入以*foo*开头的子目录中

z ~/foo # z支持cd的传统模式
z foo/  # 进入相对路仅
z ..    # 进入上级目录
z -     # 进入之前的目录，类似导航中的返回

zi foo  # 使用交互模式使用z,需要安装`fzf`
z foo<SPACE><TAB> # 使用交互式完成
```

## 子命令

### zoxide init

`zoxide init`可以生成自动完成命令。添加了对各个平台的支持。下面以`zsh`为例：

添加下面的内容到你的`zsh`配置文件中(通常是`~/.zshrc`):
```bash
eval "$(zoxide init zsh)"
```

### zoxide add [PATHS]

`zoxide add [PATHS]`用于手动添加一个目录到`zoxide`数据库中，或提升是排名。

### zoxide remove [PATHS]

`zoxide remove [PATHS]`用于手动把一个目录从`zoxide`的数据库中删除。

### zoxide edit

使用`zoxide edit`可以手动编辑`zoxide`的数据库，比如把一个目录从数据库中删除，手动修改一个目录在数据库中的排名。

### zoxide query

使用`zoxide query [OPTIONS] [KEYWORDS]`可以查询一个目录在数据库的的情况

OPTIONS说明：
* --all     显示已经通过`remove`删除的目录
* -i, --interactive   以交互式的方式查询
* -l, --list 列出所有符合关键字的查询结果
* -s, --source 在查询结果中列表分数
* --exclude <path> 从结果中排除<path>

