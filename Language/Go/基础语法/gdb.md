# Go中gdb的调试

## 常用命令操作

### 查看支持的语言列表

```shell
<gdb> set language
```

### 显示源码

```shell
# 显示当前附件的10行
<gdb> list
# 显示20行周围的10行
<gdb> list 20
# 显示上一个list代码之前的10行
<gdb> list -
# 查看main函数
<gdb> list main
# 查看1-100行
<gdb> list 1,100
```



### 设置断点

```

```

