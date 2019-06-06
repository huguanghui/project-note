[TOC]

# gtags使用

# 链接

[GLOBAL官网](https://www.gnu.org/software/global/)

[工具使用笔记](http://blog.chinaunix.net/uid-20416834-id-120183.html)

## 安装

### 直接安装

```c++
$ sudo apt-get install global
```

### 源码安装

```c++
# 安装依赖库
$ sudo apt build-dep global
$ sudo apt install libncurses5-dev libncursew5-dev
# 下载源码
$ wget https://ftp.gnu.org/pub/gnu/global/global-6.6.tar.gz
# 编译和安装
$ ./configure --with-sqlite3
$ make -j4
$ sudo make install
```

## 使用



## VSCode中gtags使用