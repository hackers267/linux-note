# 权限管理

## ACL权限管理

我们知道，在 *linux* 中基本的权限分配是以 *用户，用户组和其他用户* 的形式进行管理的。但如果我们需要为某个特定的用户分配特定的权限，就需要使用到 *ACL* 权限管理了。

*ACL* 是 *Access Control Lists* 的缩写。它允许把任意的磁盘文件授权给任意用户或组。

要启用 *ACL* ,文件系统在挂载时必须要加入 *acl* 参数。要开机时自动启用 *ACL* ，可以通过编辑 `fstab` 文件来实现。

### 使用

为用户设定权限(*user* 是用户名或 *UID* ):

```
  setfacl -m "u:user:permission" <file/dir>
```

为用户组设定权限(*group* 是用户组或 *GID* )

```
  setfacl -m "g:group:permission" <file/dir>
```

为其他用户设定权限

```
  setfacl -m "other:permission" <file/dir>
```

> 提示：
> - 可以通过添加 `--test` 参数来测试该命令的结果
> - 要递归地将操作应用到所有的文件和目录上，使用 `-R/--recurise` 参数 

允许所有新创建的 *文件或目录* 仌父目录继承条目(这不会影响将 *复制* 到目录中的文件):

```
  setfacl -dm "条目" <dir>
```

删除权限:

```
  setfacl -x "user/group" <file/dir>
```

删除默认权限

```
  setfacl -k <file/dir>
```

删除所有 *ACL*  权限(拥有者、用户组和其他用户的权限将被保留)

```
  setfacl -b <file/dir>
```

### 查看 *ACL* 

要显示 *ACL* 权限，可以使用

```
  getfacl <file/dir>
```
 

