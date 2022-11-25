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

- d 删除
- r 回复
