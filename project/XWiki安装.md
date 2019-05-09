[TOC]

# XWiki安装

> XWiki是一个基于Java,运行于Servlet容器(像Tomcat, Jetty, JBoss, WebLogic, WebSphere等)中.它使用了关系数据库.可以使用MySQL, PostgreSQL,等数据库.
>
> 如果你是更新一个已存在的XWiki安装,查阅[Upgrade instructions page](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Upgrade).
>
> 在[installation methods](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/#HInstallationMethods)中挑一种方式进行安装.完成安装后,通过学习 [Admin Guide](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/) 中的其他主题去配置和增强wiki的安全性.

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