[TOC]

# mysql

## 安装

### archlinux

```shell
$ sudo pacman -S mysql
$ sudo pacman -S mysql-workbench
$ sudo mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
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

