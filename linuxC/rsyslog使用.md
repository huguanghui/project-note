[TOC]

## 基于rsyslog搭建日志服务系统

## 链接

[rsyslog](https://www.rsyslog.com/category/guides-for-rsyslog/)

## 组成

- 客户端
- 日志服务器
- 日志存储数据库服务器

### 客户端

### 日志服务器

```
#/etc/rsyslog.conf
$ModLoad imudp
$UDPServerRun 514
```

### 数据库服务器