[TOC]

# Go的源码安装

[github镜像地址](https://github.com/golang)

[参考](http://www.cnblogs.com/dyh004/p/9669406.html)

[golang的arm安装](https://blog.csdn.net/coroutines/article/details/39522143)

```shell

设置GOROOT：export GOROOT=/usr/local/go

设置PATH：export PATH=$PATH:$GOROOT/bin

编译arm：CGO_ENABLED=0 GOARCH=arm GOOS=linux ./make.bash

成功之后，运行go tool，可以看到有5g和5l。

```

# 九大特性

- 垃圾回收机制

- 更丰富的内置类型（map, slice）
- 函数多返回值 （_）
- 错误处理 
- 类型和接口
- 匿名函数和闭包
- 并发编程 
- 反射
- 语言交互性

# 包和工具

> 包的概念->导入的路径->包声明->导入声明->包的匿名导入->包和命名->工具

# 测试

测试函数,基准测试,示例函数



