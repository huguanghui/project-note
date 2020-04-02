[TOC]

# 使用docker搭建nginx的开发环境

## 安装nginx的官网镜像

```shell
$docker search nginx                         # 查看nginx的官方镜像文件
$docker pull nginx                           # 下载nginx的官方镜像文件
$docker images
```

## 测试nginx的镜像

```shell
$docker run -p 8080:80 -d docker.io/nginx  //将80端口映射为8080
```

## 使用

```shell
$docker run -p 80:80 -d -v /home/hgh/html:/usr/share/nginx/html nginx
```

