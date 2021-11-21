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

## 安装Sougou中文输入法

```
sudo apt-get purge fcitx-ui-qimpanel
```

## 截面优化

[参考](https://zhuanlan.zhihu.com/p/183861786)

[dwm](https://www.baidu.com/s?wd=dwm%E7%BC%96%E8%AF%91)

### 程序选择器-dmenu

### 屏幕壁纸-feh

## variety

### 窗口美化-picom

### 文本搜索

```
apt-get install silversearcher-ag
```

## 终端st

```shell
git clone git@github.com:huguanghui/st.git
```

X11/Xlib.h

```shell
$ sudo apt-get install libx11-dev 
```

X11/xpm.h：no such file or directory

```shell
$ sudo apt-get install libxpm-dev
```

X11/Xft/Xft.h: no such file or directory

```shell
$ sudo apt install libxft-dev
```

出现了一个奇怪问题, 安装好st后问题就解决了

现象: st终端 ssh 远程登陆后 tmux 开启后,执行neovim后tmux整个崩溃了

## LNMP搭建

