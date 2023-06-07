# 用户管理

在下面的示例中，以用户`oracle`为例：

## 添加用户

```
useradd oracle
```

## 为已经存在的用户添加/修改密码

```bash
passwd oracle
```

## 为已经存在的用户添加home目录

```bash
mdkr /home/oracle
chown oracle:oracle -R /home/oracle
usermod -d /home/oracle oracle
```
