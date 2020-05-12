​		

[TOC]

## Linux上Go的安装

## 下载地址

[下载地址](https://studygolang.com/dl)

## 版本变更

| 版本号 | 日期 | 修改点 |
| :----: | :--: | :----: |
| 1.12.7 |      |        |
|        |      |        |
|        |      |        |



## 安装命令

[官网教程](http://docs.studygolang.com/doc/install)

```shell
$ tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
$ export PATH=$PATH:/usr/local/go/bin
$ export GOROOT=$(go env GOROOT)
$ export GOPATH=$(go env GOPATH)
$ export PATH=$PATH:$GOPATH/bin
```

go代理设置

[golang国内代理设置](https://www.cnblogs.com/rongfengliang/p/11419210.html)

## 解决国内 go get 无法下载的问题

```
# 使用七牛云module
$ go env -w GO111MODULE=on
$ go env -w GOPROXY=https://goproxy.cn,direct
# 使用阿里module
$ go env -w GO111MODULE=on
$ go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
```

## vim 的 go 插件

### vim-go

> 代码高亮和语法检测插件

#### 安装

```vim
Plug 'fatih/vim-go', {'do': 'GoUpdateBinaries'}
```

### vim-gocode

> 代码提示插件

#### 安装

```vim
Plug 'Blackrush/vim-gocode'
```

### tagbar

> 显示代码结构的插件

#### 安装

```vim
Plug 'majutsushi/tagbar'
```

