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

### gitlab的控制命令

| 命令功能                   | 执行命令                                       |
| -------------------------- | ---------------------------------------------- |
| 重启配置，并启动gitlab服务 | sudo  gitlab-ctl reconfigure                   |
| 启动所有 gitlab            | sudo gitlab-ctl start                          |
| 重新启动GitLab             | sudo  gitlab-ctl restart                       |
| 停止所有 gitlab            | sudo gitlab-ctl stop                           |
| 查看服务状态               | sudo gitlab-ctl status                         |
| 查看Gitlab日志             | sudo gitlab-ctl tail                           |
| 修改默认的配置文件         | sudo vim /etc/gitlab/gitlab.rb                 |
| 检查gitlab                 | gitlab-rake gitlab:check SANITIZE=true --trace |

## 汉化

```
$ cp -r /opt/gitlab/embedded/service/gitlab-rails{,.ori} 
$ git clone https://github.com/larryli/gitlabhq.git
$ sudo gitlab-ctl stop
$ sudo cp -rf /root/gitlabhq/* /opt/gitlab/embedded/service/gitlab-rails/
$ sudo gitlab-ctl start 
```

