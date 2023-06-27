# erdtree(erd)

`erdtree(erd)`是一个现代的、充满活力的，多线程文件树视化工具和磁盘使用分析器。在默认情况下，它不显示隐藏文件和符合`.gitignore`规则的文件。


`erdtree`是`tree`命令的现代替代器：
* 提供最小且用户友好的命令行工具
* 默认情况下不显示隐藏文件和符合`.gitignore`规则的文件
* 默认以人数可读的格式显示文件大小
* 以并行的方式遍历日期
* 默认使用ANSI颜色显示文件

## 使用

`erd`的使用有下面几个选项可以使用：

* `-i, --no-ignore`             不忽略`.gitignore`文件；
* `-l, --level <NUM>`           显示的目录的最大深度
* `-t, --threads <THREADS>`     并行的进行数，默认为3
* `-s, --sort <SORT>`           显示目录的排序方式，默认为`size`，可选值为：[`name`,`rname`,`size`,`rsize`,`access`,`raccess`,`create`,`rcreate`,`mod`,`rmod`]
* `-., --hidden`                显示隐藏文件
* `-g, --glob <GLOB>`           显示符合或不符合`GLOB`的内容，不区分大小写
* `--iglob <IGLOB>`             显示符合或不符合`GLOB`的内容，区分大小用
* `-h, --help`                  显示帮助内容
* `-V, --version`               显示版本
