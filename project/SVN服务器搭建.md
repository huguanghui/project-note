[TOC]

# SVN服务器搭建

## SVN仓库

### 创建项目

```shell
# 创建基地目录
$mkdir /home/svn
# 创建项目
$svnadmin create /home/svn/project
```

### 创建组

```shell
# 创建 subversion
$ addgroup subversion
# 将 www-data 加入 subversion 组中
$ usermod -G subversion -a www-data
# 查看用户权限
$ more /etc/group | grep subversion
```

### 修改项目权限

```shell
$ chown -R root:subversion  /home/svn/project
$ chmod -R g+rws  /home/svn/project 
```

### 访问库

```shell
$ svn co file://localhost/home/svn/project
```

## 独立服务器搭建

```shell
$ svnserve -d --listen-port 9999 -r /home/svn
```

## 权限配置

### SVN配置

```shell
# svnserve.conf
anon-access = none
auth-access = write
password-db = passwd
authz-db = authz
realm = www
```

### 添加用户和密码

```shell
# passwd
[users]
admin = 123456
```

### 添加组和权限

```shell
# authz
[groups]
g1 = admin

[/foo/bar]
@g1 = r
```

## 开机自启动

```shell
# 加入启动项
# vim /etc/rc.local
```

