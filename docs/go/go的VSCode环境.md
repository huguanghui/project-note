[TOC]

## 环境插件问题

> 出现Installing github.com/sqs/goreturns FAILED的安装问题

分析原因: 依赖https://golang.org/x/tools,无法获取导致.

解决办法: 建立$GOPATH/src/golang.org/x目录,本地通过github的镜像仓库来获取

```shell
$ cd $GOPATH/src
$ mkdir -p golong.org/x
$ cd golang.org/x
$ git clone  https://github.com/golang/tools.git
```

