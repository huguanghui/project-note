[TOC]

## 安装

### 依赖包

- [python](https://www.python.org/) 2.6-3.0
- [setuptools](https://pypi.org/project/setuptools)>=0.6
- [Genshi](https://pypi.org/project/Genshi)>=0.6

### 数据库

- SQLite

## 版本管理

- SVN
- GIT

## WebServer

- Apache
- a FastCGI-capable webserver
- an AJP-capable webserver
- a CGI-capable web server 

## 其他依赖

- Babel
- docutils
- Pygments
- pytz

## 搭建工程环境

> Trac环境是Trac存储诸如维基页面，票据，报告，设置等信息的后端.这个环境是一个包含了可读的配置文件和其他文件和目录.

使用trac-admin命令创建一个新环境.

```shell
$ trac-admin /path/to/myproject initenv
```

