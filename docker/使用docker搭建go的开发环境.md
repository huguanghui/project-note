[TOC]

# 使用Docker搭建Go的开发环境

## 配置docker的镜像仓库

```shell
$docker info            # 查看docker的信息
hgh@hgh-Macmini:~$ cat /etc/docker/daemon.json 
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
# 修改为
hgh@hgh-Macmini:~$ cat /etc/docker/daemon.json 
{
  "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
$systemctl restart docker    #重启docker服务
```



## 安装go的官方镜像

```shell
$docker search golang              # 查看golang的官方镜像路径
$docker pull golang                # 下载golang的官方镜像
```

## 测试golang镜像

```shell
$run -it --rm golang bash         # 测试go镜像
```

## 使用golang镜像

> 让数据持久化,解决方式:将主机的目录映射到容器中,直接映射目录会有权限限制,使用--privileged参数给容器放权.

```shell
[root@fengbo golang]$ docker run \    # 执行 docker 命令，创建一个新的容器并运行这个容器
> -it \                               # 使用交互模式
> --rm \                              # 当退出这个容器时，系统自动删除这个容器
> -v /home/hgh/golang/go:/go \            # 把主机的目录 '/root/golang/go' 映射为容器内的目录 '/go'
> -v /home/hgh/golang/code:/code \        # 把主机的目录 '/root/golang/code' 映射为容器内的目录 '/code'
> --privileged \                      # 给这个容器超级权限，否则无法操作上面映射进去的两个目录
> golang \                  		  # 基于镜像 'docker.io/golang' 创建容器
> bash                                # 在容器内执行命令 'bash'
```

```shell
# 完整命令
$docker run -it --rm -v /home/hgh/golang/go:/go -v /home/hgh/golang/code:/code --privileged golang bash
```

