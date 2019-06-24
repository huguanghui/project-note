[TOC]

# ubuntu的问题整理

## g++版本

```shell
# 安装基础全家桶
$ apt-get install build-essential
```

## 查看 gcc 编译器的头文件加载路径

```shell
$ echo 'main(){}'|gcc -E -v -
```

