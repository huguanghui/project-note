[TOC]

# 相关资源

[docker](https://www.docker.com/)

[docker入门](https://yeasy.gitbooks.io/docker_practice/content/)

[使用docker搭建linux开发环境](https://www.ctolib.com/topics-133553.html)

# docker-compose的使用

> Compose是一个用户定义和运行多个容器的Docker应用程序.

- Dockfile中定义你的应用环境
- docker-compose.yml中定义组成应用程序的服务.
- docker-compose up 启动整个应用程序

# github+daocloud环境搭建

[Daocloud](https://dashboard.daocloud.io/build-flows)

# DockerFile容器解析

[博客](https://www.cnblogs.com/liangjindong/p/9409697.html)

# 镜像使用

## 创建Dockerfile

## 构建镜像

```shell
docker build -t hellomygohttp . 
```

## 基础操作

```shell
# 运行镜像
$ docker run --name mygohttp -p 8080:8080 -d mygohttp
# 停止服务
$ docker stop mygohttp
# 删除实例
$ docker rm mygohttp
# 删除镜像
$ docker rmi mygohttp
```



