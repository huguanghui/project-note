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

##### gtags生成索引

```shell
# 1.直接生成索引文件
$ gtags
# 2.存放在外部目录,可以修改 MAKEOBJDIRPREFIX
$ mkdir -p /usr/obj + 当前绝对路径
$ gtags /usr/obj + 当前绝对路径
# 3.扩展路径, 使用 GTAGSLIBPATH 或软连接
$ export GTAGSLIBPATH=/usr/src/lib:/usr/src/sys
```

##### global使用

|           选项            |               描述               |
| :-----------------------: | :------------------------------: |
|            -a             |           显示绝对路径           |
|            -r             |             查看调用             |
| POSIX regular expressions |        POSIX的正则表达式         |
|            -x             |           显示详细信息           |
|            -s             |  列出没有在GTAGS中定义的symbols  |
|            -g             |        定义有指定格式的行        |
|            -O             |        只在text文件中搜素        |
|            -o             |     同时搜索源文件和text文件     |
|            -l             |        只在当前目录下检索        |
|            -P             | 列出符合指定格式的文件名称的列表 |
|            -f             |      列出指定文件的所有索引      |
|                           |                                  |



### 插件

## 自动索引

## 文件切换

## 动态检查

## 修改比较



