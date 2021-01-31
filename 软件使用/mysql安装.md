[TOC]

# mysql

## 安装

### archlinux

```shell
$ sudo pacman -S mysql
$ sudo pacman -S mysql-workbench
$ sudo mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
```

### Debian

```shell
$ sudo apt-get install mysql-server
```

## 启动

```shell
$ sudo systemctl start mysqld.service
$ sudo systemctl enable mysqld.service
# 连接服务器
$ mysql -uroot -p
# 修改密码
$ sudo mysqladmin -p password "new_password"
```

## 使用

```shell
# 查询数据库
$ show databases;
# 创建数据库名称
$ CREATE DATABASE [名称];
# 删除数据库
$ DROP DATABASE [名称];
# 选择数据库
$ USE [名称];
# 创建表

```

