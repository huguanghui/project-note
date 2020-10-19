[TOC]

## 简介

> 用于梳理最近的问题, 和提高效率的方法

## 20201012

- [x] ag的字符串匹配搜索
- [x] 常用的网络接口命令
- [x] 目标文件分析

### 目标文件分析

```shell
# 分析程序, 动态库和静态库的编译器版本
# 静态库拆分
## ar: 建立或修改备份文件
$ ar x *.a
# 静态库和动态库中的接口查询
## nm工具: 列举目标文件中的符号
$ nm -A *.a
$ nm -D *.so
# 可执行程序依赖动态库分析
## ldd 显示动态库的依赖情况
```

### 网络命令

```shell
# 查看路由信息
# 查看监听端口
# 查看端口被哪个进程占用
```

### ag的字符串匹配处理

[正则表达式使用](https://blog.csdn.net/wx_start_ag/article/details/79566952)

```shell
# 操作格式
Usage: ag [FILE-TYPE] [OPTIONS] PATTERN [PATH]
在 PATH 路径下按 PATTERN 进行递归搜索
```

## 20201013

- [x] revert-i-search的用法
- [x] shell下快读移动技巧 (ctrl +a ctrl + e ctrl + w)

## 20201015

- [x] apt的软件包搜索
- [x] ranger图片预览

### apt操作

```shell
$ apt-cache search 包名
```

### ranger图片预览

```shell
使用 ueberzug 进行图像预览, 但测试虚拟机不支持pip3, 软件安装失败
```

## 20201016

- [x] 按格式搜索文件
- [ ] vim录制宏操作

## 20201019

- [ ] 计算机原理_进程
- [ ] flash操作