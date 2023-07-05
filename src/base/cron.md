# 定时任务

当我们在使用linux的时候，免不了要使用到定时任务去做一些东西。这个时候，我们就需要使用linux的定时任务的功能了。

## fcrontab

在linux中管理定时任务的工具有很多，这里以`fcrontab`为例来说明定时任务的使用。

frontab的常用的命令有以下几个：

- `fcrontab -l`  列出用户当前的定时任务
- `fcrontab -r`  移除用户当前的定时任务
- `fcrontab -e`  编辑用户当前的定时任务
- `fcrontab -u user`  指定用户名称

## crontab

`crontab`是linux中另一个常见的定时任务管理工具。

### crontab的使用
其使用如下：
```shell
crontab [-u username] // 省略用户表州操作当前用户的crontab
	-e (编辑工作表)
	-l (列出工作表里的命令)
	-r (删除工作表)
```

crontab的使用是非常简单的，其命令的构成形式为时间 + 动作，其时间格式为分、时、日、月、周五种，中间以空格分开。每个时间对应着四种不同操作符： * / - , 。其含义如下：
  - * 取值范围内的所有数字
  - / 每隔多长时间 /2 表示每过2
  - - 范围跨度，如8-11表示从8到11
  - , 并列的数字，如 15,30 表示 15和30

示例：
```shell
* * * * * myCommand // 每分钟执行一次 myCommand
30 * * * * myCommand // 每个小时的第30分钟执行一次 myCommand
15,30 * * * * myCommand //每个小时的第15分钟和第30分钟分别执行一次 myCommand
0 0-1 * * * myCommand  // 每天的0-1点的第0分钟执行一次
0 0 */2 * * myCommand // 每隔2天的凌晨0点执行一次
```

### crontab的配置文件

在系统中，crontab有存在一些的配置文件。其作用如下：

- /var/spool/cron/ 目录下存放的是每个用户包括root的crontab任务，每个任务以创建者的名字命名。
- /etc/crontab 这个文件负责调度各种管理和维护任务
- /etc/cron.d/ 这个目录用来存放任务要执行的crontab文件或脚本
- /etc/cron.hourly 每小时执行的任务
- /etc/cron.daily	每天执行的任务
- /etc/cron.weekly 每星期执行的任务
- /etc/cron.monthly 每月执行的任务