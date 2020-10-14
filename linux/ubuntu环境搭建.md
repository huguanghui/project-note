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

