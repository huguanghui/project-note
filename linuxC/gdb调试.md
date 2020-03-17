[TOC]

# GDB调试

## 链接

[gdb在线手册](https://sourceware.org/gdb/onlinedocs/gdb/)

[100个gdb调试技巧](https://wizardforcel.gitbooks.io/100-gdb-tips/content/)

## 生成core文件

```shell
$ ulimit -c unlimited 
```

## 常用调试命令

### 加载程序

```
# 启动gdb
$ gdb -q
# 启动程序
$ gdb + 程序名 或者 gdb 后 file 程序名
```

### 环境

```
# 优化结构体的打印
$ set print pretty on
# gdb输出信息较多时,gdb会暂停输出
$ set pagination off 或 set height 0
# 显示动态库信息
$ info sharedlibrary
```

### 断点

```shell
# 设置断点
$ b file:linenum
# 设置临时断点
$ tb file:linenum
# 设置条件断点
$ b file:linenum if cond
# 忽略断点
$ ignore bnum count
# 删除断点
$ delete
# 查看断点信息
$ info breakpoints
# 列出当前运行的行号
$ bt
```

## 增加效率

### 配置

## 40天连续 gdb 的使用经验打卡

- [x] 20200313
- [x] 20200314
- [x] 20200315