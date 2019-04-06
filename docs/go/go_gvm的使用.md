[TOC]

# GVM使用

[GVM](https://github.com/moovweb/gvm)

[Go GVM管理](https://www.ctolib.com/gvm.html)

## 安装

```shell
$ bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer) 
```

## 安装Go版本

```shell
$ gvm install go1.4 -B                   // 二进制方式安装
$ gvm list                               // 查看已安装的Go版本
$ gvm use go1.4                          // 当前选择的go1.4版本的环境
```

## GVM的项目管理

```shell
$ mkdir -p ~/goproj/baozou
$ cd ~/goproj/baozou
$ gvm pkgset create --local
$ gvm pkgset use --local
$ mkdir src
```

## GVM安装失败的解决

执行gvm install go1.4失败,国内无法访问到google服务器原因.

解决办法,替换为github的地址

```shell
# ~/.gvm/scripts/install中GO_SOURCE_URL的地址修改为https://github.com/golang/go
GO_SOURCE_URL=https://github.com/golang/go
```

