[TOC]

# XWiki安装

> XWiki是一个基于Java,运行于Servlet容器(像Tomcat, Jetty, JBoss, WebLogic, WebSphere等)中.它使用了关系数据库.可以使用MySQL, PostgreSQL,等数据库.
>
> 如果你是更新一个已存在的XWiki安装,查阅[Upgrade instructions page](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Upgrade).
>
> 在[installation methods](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/#HInstallationMethods)中挑一种方式进行安装.完成安装后,通过学习 [Admin Guide](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/) 中的其他主题去配置和增强wiki的安全性.

[XWiki](https://www.xwiki.org/xwiki/bin/view/Main/)

## 安装

### 前提

#### 不同版本对Java的依赖

| KWiki的版本 | Java版本 |
| :---------: | :------: |
|    >=8.1    |  Java 8  |
|    <8.1     |  Java 7  |
|     <6      |  Java 6  |
|    <11.3    |  Java 8  |
|   >=11.3    | Java 11  |

#### Servlet容器版本

> 详情查看 [Servlet Containers officially supported by XWiki devs](https://dev.xwiki.org/xwiki/bin/view/Community/ServletContainerSupportStrategy/)

| KWiki的版本 | Servlet版本 |
| :---------: | :---------: |
|    <7.0     |     2.4     |
|    其他     |    3.0.1    |

#### 数据库

> 详情查看[databases offically supported by XWiki devs](https://dev.xwiki.org/xwiki/bin/view/Community/DatabaseSupportStrategy)

| KWiki的版本 | JDBC版本 |
| :---------: | :------: |
|    <7.0     |  JDBC 3  |
|    其他     |  JDBC 4  |

#### 浏览器

>可以使用浏览器访问,详情见 [browsers offically supported by XWiki devs](https://dev.xwiki.org/xwiki/bin/view/Community/BrowserSupportStrategy)

#### 存储

>见 [Performance Guide](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Performances/)中的[Memory section](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Performances/#HMemory).

#### CPU和RAM

> 见 [CPU and RAM](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Performances/#HSizing)

#### 版本记录

> 见[release notes](https://www.xwiki.org/xwiki/bin/view/ReleaseNotes/)

## 配置

## 更新



## 安装

### 使用docker进行安装

[官方提供的镜像](https://hub.docker.com/_/xwiki/)

[xwiki docker镜像的使用](<https://github.com/xwiki-contrib/docker-xwiki/blob/master/README.md>)

#### 搭建步骤

##### 1. 新建一个专用的docker网络

```shell
$ docker network create -d bridge xwiki-nw
```

##### 2.  数据库环境
> 然后为数据库运行一个容器，并确保它配置为使用UTF8编码。

开箱即用支持以下数据库：

- MySQL
- PostgreSQL

此处我们使用MySQL方式

创建/my/own/mysql目录

```shell
$ mkdir -p /home/hgh/xwiki/mysql
```

运行MySQL容器

```shell
# 配置MySQL容器以将其数据保存在/my/own/mysql目录中的localhost上
$ docker run --net=xwiki-nw --name mysql-xwiki -v /home/hgh/xwiki/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=xwiki -e MYSQL_USER=xwiki -e MYSQL_PASSWORD=xwiki -e MYSQL_DATABASE=xwiki -d mysql:5.7 --character-set-server=utf8 --collation-server=utf8_bin --explicit-defaults-for-timestamp=1
# 在MySQL 5.6.6中引入了 explicit-defaults-for-timestamp 参数，因此仅适用于该版本及更高版本。如果您使用的是较旧的MySQL版本，请使用以下代码
$ docker run --net=xwiki-nw --name mysql-xwiki -v /my/own/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=xwiki -e MYSQL_USER=xwiki -e MYSQL_PASSWORD=xwiki -e MYSQL_DATABASE=xwiki -d mysql:5.7 --character-set-server=utf8 --collation-server=utf8_bin
```

##### 3. 开始运行XWiki

创建本地目录

```shell
$ mkdir -p /home/hgh/xwiki/xwiki
```

MySQL方式

```shell
# 
$ docker run --net=xwiki-nw --name xwiki -p 8080:8080 -v /home/hgh/xwiki/xwiki:/usr/local/xwiki -e DB_USER=xwiki -e DB_PASSWORD=xwiki -e DB_DATABASE=xwiki -e DB_HOST=mysql-xwiki xwiki:lts-mysql-tomcat
```

此时，XWiki应该以交互式阻止模式启动，允许您在控制台中查看日志。如果您希望以“分离模式”运行它，只需在上一个命令中添加“-d”标志即可。

```shell
docker run -d --net=xwiki-nw ...
```

#### 使用 docker-compose方式（TODO）

##### MySQL 方式

#### 使用 docker swarm方式（TODO）

### Linux上的安装

[安装教程](https://www.unixmen.com/xwiki-installation-linux/)

