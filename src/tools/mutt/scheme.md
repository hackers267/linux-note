# 搭配方案

方案1: *fetchmail* + *sendmail* + *procmail* + *vim* 精简

方案2: *offlineimap* + *msmtp* + *maildrop* + *helix*  现代化

## 方案1

### fetchmail

*fetchmail* 的安装和配置

安装 *fetchmail*:

```bash
  paru -S fetchmail
```

配置 *fetchmail*:

示例文件：

```
set daemon 600
defaults protocol POP3
keep
poll pop.AAA.com uidl user me@AAA.com password 1234 
mimedecode
mda "/usr/bin/procmail -f %F" 
#
poll pop.BBB.com uidl user me@BBB.com ssl password 4567
#    
mimedecode
mda "/usr/bin/procmail -f %F" 
```

在上面的配置中， `set daemon 600` 设置每600(即10分钟)秒在后台接收一次邮件 , `keep` 表示只收取未读取邮件，`default protocol POP3` 表示默认协议使用 *POP#*.
使用 *poll* 来分隔不同的收件配置。

   
- 各种参数可以不按顺序，也可以不在一行。 空格隔开每个参数，poll隔开每个账户。
- *poll* 后面是邮件服务器的地址，一般是 *pop.xxx.com*
- protocol后面是收件协议，一般是pop或pop3
- user后面是用户名，可以是username，也可以是邮箱地址
- password后面是密码
- 以上是必填，其它都不是必要的
- 四选一：fetchall, nofetchall, keep, nokeep
- mimedecode用来自动解码MIME
- mda后面指定本机安装的邮件过滤分类程序。如果不填，则收取的邮件在本地不会保存。可以用$ which procmail查一下路径 
  
### procmail

*procmail* 在这里扮演的角色是用于存储邮件,分类和过滤邮件。

*procmail* 安装:

```bash
  paru -S procmail
```
 
配置文件示例：

```
MAILDIR=$HOME/Mail
DEFAULT=$MAILDIR/inbox
VERBOSE=off
LOGFILE=$HOME/.procmail.log
```

sendmail 是 *linux* 系统一般会自带，在 *mutt* 中不需要特殊配置  

## 方案2


