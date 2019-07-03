[TOC]

# ctags使用

## 链接

[ctags官网](http://ctags.sourceforge.net/)

## 安装

### ubuntu

```shell
$ sudo apt-get install ctags
```

## 使用

```
$ ctags -R -f .tags
```

## VSCode的CTags Support插件的使用

### 导航到定义

> 按键ctrl + t

### 查看导航历史

> 按键ctrl + shift +t

### 其他两个特性

- 删除所有导航历史
- 删除单个导航历史

f1, 输入Ctags

## 命令使用

```shell
# 查看帮助
$ ctags --help
# 列出支持的语言
$ ctags --list-languages
# 列出语言和后缀的映射关系
$ ctags --list-maps
# 将tags写到指定文件.tags中
$ ctags -f .tags
# 递归目录
$ ctags -R  // 等价于 ctags --recurse
# 查看可识别的语法元素
$ ctags --list-kinds
$ 只对 c 相关的文件进行分析
$ find . -type f \( -name "*.c" -o  -name "*.cpp" -o -name "*.hh" -o -name "*.h" \) > filelist.txt
# 对指定文件进行分析
$ ctags -L filelist.txt
```

## 查询命令

```
$ vim -t 需要查询的变量或函数名
```

