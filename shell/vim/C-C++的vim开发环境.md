[TOC]

# C/C++的Vim开发环境搭建

## 符号索引

### 工具

#### gtags的编译安装

[gtags的官网](http://www.gnu.org/software/global/)

```shell
wget http://tamacom.com/global/global-6.6.3.tar.gz
./configure
make
make install
```

[ncurses下载](http://ftp.gnu.org/gnu/ncurses/ncurses-6.1.tar.gz)

```shell
#依赖
## curses
https://blog.csdn.net/costeeer/article/details/81268046
## 源码安装
$ wget http://ftp.gnu.org/gnu/ncurses/ncurses-6.1.tar.gz
$ ./configure --with-shared --without-debug --without-ada --enable-overwrite
$ make
$ make install
```

#### 基础使用

```shell
# 1.直接生成索引文件
$ gtags
# 2.存放在外部目录,可以修改 MAKEOBJDIRPREFIX
$ mkdir -p /usr/obj + 当前绝对路径
$ gtags /usr/obj + 当前绝对路径
# 3.扩展路径, 使用 GTAGSLIBPATH 或软连接
$ export GTAGSLIBPATH=/usr/src/lib:/usr/src/sys
```



### 插件

## 自动索引

## 文件切换

## 动态检查

## 修改比较



