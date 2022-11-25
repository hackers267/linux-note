# Mutt

## 命令行

- a 指定附件
- s 指定主题
- h 查看帮助


发送邮件
```shell
echo "hello,This email from mutt" | mutt -s "Example" -a ./example.txt -- hello@world.com
```

## 交互式命令

- d 为当前邮件添加删除标记
- u 撤销当前邮件的删除标记
- @ 显示当前邮件的详情地址
- a 为当前邮件的发送人添加别名
- b 把当前邮件转发另一个用户
- c 打开另一个文件夹(比如发件文件夹)
- e 编辑原始邮件
- m 撰写新邮件
- g 回复给所有收件人
- s 保存邮件/附件到邮箱/文件
- r 回复当前邮件
- &lt;Tab&gt; 跳转到下一个未读邮件
- &lt;Enter&gt; 查看邮件内容
