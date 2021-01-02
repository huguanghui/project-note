[TOC]

# ubuntu的环境搭建

## I3桌面

[ubuntu+i3wm搭建](https://blog.csdn.net/qq907482638/article/details/54576516)

[参考](https://www.bilibili.com/read/cv3120815/)

## 常用软件

## 字体安装

### 查询

```shell
# 查询
$ fc-list
# 查询中文字体
$ fc-list :lang=zh
```

### 拷贝到指定路径

```shell
$ sudo mkdir -p /usr/share/fonts/custom
# 拷贝
# 修改权限
$ sudo chmod 744 /usr/share/fonts/custom/*.ttf

# 生成核心字体信息
$ sudo mkfontscale
$ sudo mkfontdir
$ sudo fc-cache -fv
```

## 更换国内镜像源

[链接](https://blog.csdn.net/wzyaiwl/article/details/88571414)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

```
deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main
 
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main
 
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
 
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe
```

```
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
```

## DWM环境安装

[ubuntu的官方仓库](http://manpages.ubuntu.com/manpages/xenial/man1/dwm.1.html#description)