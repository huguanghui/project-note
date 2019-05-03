[TOC]

# Nginx+fcgi环境搭建

## 计划目的

- [ ] unix域套接字进行通讯
- [ ] 测试unix域套接字的速度,与IPv4的TCP和UDP速度进行对比
- [ ] 将fcgi中的unix域套接字的实现代码独立出来

## 环境准备

- nginx环境
- fcgi开源包

## 搭建步骤

### Nginx配置

使用nginx中的fastcgi特性

```
fastcgi_pass unix:/dev/shm/php-cgi.sock;
fastcgi_pass unix:/tmp/php-fcgi.sock;
```

```
location /api/v2/ {
	fastcgi_pass unix:/tmp/test.sock;
	fastcgi_param SCRIPT_FILENAME  /scripts$fastcgi_script_name;
	include fastcgi_params;
}

```

### fcgi库的编译

