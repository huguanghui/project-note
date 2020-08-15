[TOC]

# GitLab 搭建

## 环境

ubuntu 16.04

## 命令

[gitlab 社区版安装](https://www.jianshu.com/p/3a4e75ef69a8)

```shell
# 安装依赖
$ sudo apt-get update
$ sudo apt-get install -y curl openssh-server ca-certificates
# 安装邮件
$ sudo apt-get install -y postfix
# 下载 gitlab 离线包
$ wget https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/debian/pool/stretch/main/g/gitlab-ce/gitlab-ce_10.7.1-ce.0_amd64.deb
$ sudo dpkg -i gitlab-ce_10.7.1-ce.0_amd64.deb
# apt 方式
# 添加秘钥
$ curl https://packages.gitlab.com/gpg.key 2> /dev/null | sudo apt-key add - &>/dev/null
# 添加软件源
$ sudo echo "deb http://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/debian stretch main" > /etc/apt/sources.list.d/gitlab-ce.list
# 更新并安装
$ sudo apt-get update
$ sudo apt-get install gitlab-ce
```

