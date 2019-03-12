[TOC]

## FAQ

### docker image存储在哪里,以什么形式进行存储

> 当我们执行docker pull  镜像文件, 从docker hub上下载ubuntu image后, image存储在宿主机什么位置,以什么形式存储呢?

docker支持五种镜像层次的存储.driver, aufs, device mapper, btrfs, vfs, overlay.

安装docker时,默认的安装位置为/var/lib/docker.d

```shell
hgh@hgh-Macmini:/var/lib/docker$ sudo dir
builder  buildkit  containers  image  network  overlay2  plugins  runtimes  swarm  tmp  trust  volumes
```

### docker rmi报错

> hgh@hgh-Macmini:~$ docker rmi hello-world
> Error response from daemon: conflict: unable to remove repository reference "hello-world" (must force) - container e202f070bb3d is using its referenced image 4ab4c602aa5e

解决办法

使用docker rmi -f 进行强制删除