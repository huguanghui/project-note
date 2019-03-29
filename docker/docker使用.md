[TOC]

# Docker

## 安装

```shell
$sudo apt-get update						# 更新apt软件包索引
$sudo apt-get install \
apt-transport-https \
ca-certificates \
curl \
software-properties-common                   # 安装软件包,允许https使用镜像仓库
$curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -  # 为docker添加GPG秘钥
$sudo apt-key fingerprint 0EBFCD88
```

