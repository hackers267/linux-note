# Jq

`Jq`是一个灵活的轻量组命令行的JSON处理器，其用于处理JSON输入。其主要是使用过滤器处理合法的JSON输入，并将处理后的结果以JSON的形式输出到标准输出中。

jq的过滤器中最简单的过滤器是`.`过滤器。其可以提取JSON当中给定的字段。

## 安装

```shell
paru -S jq
```

## 语法

```shell
jq [options] <jq filter> [file...]
jq [options] --args <jq filter> [strings...]
jq [options] --jsonargs <jq filter> [JSON_TEXTS...]
```

## 选项[options]

-c                紧凑而不是漂亮的输出
-n                使用`null`作为单位输入值
-e                根据输出设置退出状态代码
-s                将所有输入读取到数组中；应用过滤器
-r                输出原始字符串，而不是JSON文本
-R                输出原始字符串，而不是JSON文本
-C                为JSON着色
-M                单色(不要为JSON着色)
-S                在输出对象上排序对象
--tab             使用制表符进行缩进
--arg a v         将变量$a设置为value<v>
--argjson a v     将变量$a设置为JSON value<v>
--slurpfile a f   将变量$a设置为从<f>读取的JSON文本数组
--rawfilw a f     将变量$a设置为包含<f>内容的字符串
--args            其余参数是字符串，而不是文件
--jsonargs        其余参数是JSON参数，而不是文件
--                终止参数处理

## 使用示例

`.`：以漂亮的方式输出：

```shell
cat package.json | jq '.'
```

提取`scripts`字段：
```shell
cat package.json | jq '.scripts'
```

获取数组中的内容：
```shell
cat package.json | jq '.keys[]'
cat package.json | jq '.keys[1]'
cat package.json | jq '.keys[0,2]'
cat package.json | jq '.keys[0:2]'
cat package.json | jq '.keys[]?'
```

构建数组/对象
```shell
cat package.json | jq '[.keys[1],keys[0]]'
```

`length`计算一个值的长度
```shell
cat package.json | jq '.keys | length'
cat package.json | jq '.keys[] | length'
```

取出对象中的键/数组中的索引
```shell
cat package.json | jq '.author | keys'
```

使用多个过滤器`,`:
```shell
cat package.json | jq '.author,.keys'
```

使用连接的过滤器`|`:
```shell
cat package.json | jq '.author | .name'
```

选择过滤`select`:
```shell
echo '[1,5,3,0,7]' | jq 'map(select(. >= 2))'
```

映射`map`:
```shell
echo '[1,2.3]' | jq 'map(.+1)'
```
