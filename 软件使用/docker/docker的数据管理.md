[TOC]

# Docker的数据管理

## 数据卷的使用

> 一个可供一个或多个容器使用的特殊目录, 它绕过了UFS,可以提供很多有用的特性.

### 查看所有的数据卷

```shell
$ docker volume ls     # 显示系统中所有的数据卷
$ docker volume inspect <name>  # 显示指定数据卷的详细信息
```

### 创建数据卷

```shell
$ docker volume create my-vol       #创建数据卷
```

### 使用数据卷

```shell
$ docker run -d -P \
    --name web \
    # -v my-vol:/wepapp \
    --mount source=my-vol,target=/webapp \
    training/webapp \
    python app.py                              # 将数据卷my-vol挂载到容器/webapp下
$ docker inspect web                           # 查看web容器的信息
```

### 删除数据卷

```shell
$ docker volume rm my-vol                    # 删除指定数据卷
$ docker volume prune                        # 删除无主的数据卷
```

