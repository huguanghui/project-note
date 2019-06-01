[TOC]

# VSCode

## 快捷键

## 包含文件和排除文件使用技巧

./nam, ./src, ./test

## 远程开发

> 该插件可以让我们通过SSH，远程设备或虚拟机，WSL，或是在Docker容器使用VSCode远程编辑.

[blog](https://code.visualstudio.com/blogs/2019/05/02/remote-development)

## VSCode中快捷键打开google浏览器

在插件栏中搜索 "open in browser"

选中*.html文件，按 alt + b

## C/C++的开发环境

- C/C++插件

- [CTags Support](https://github.com/jaydenlin/ctags-support)

## win10上搭建远程开发环境

[Remote插件](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

### 安装VSCode的Insiders版本

[地址](https://code.visualstudio.com/docs/?dv=win&build=insiders)

### 远程开发插件包分为三个

- 远程SSH
- 远程容器
- 远程WSL

### 远程SSH

#### 安装

Windows10 的 OpenSSH

“remote.SSH.showLoginTerminal”配置设为true

为了避免每次都重新输入连接信息，可以启用 ControlMaster 功能，以便 OpenSSH可以通过单个连接运行多个SSH会话.

[ssh 的配置](https://linux.die.net/man/5/ssh_config)

配置文件

```shell
Host ubuntu18.04
    User hgh
    HostName 192.168.3.145
    IdentityFile  D:\DevEnv\conf\ssh\id_rsa-remote-ssh
```

**启动 ControlMaster 的流程（未搞懂）**

1. 将下面内容添加到 SSH 配置文件中

   ```shell
   Host *
       ControlMaster auto
       ControlPath  ~/.ssh/sockets/%r@%h-%p
       ControlPersist  600
   ```

2. 运行 mkdir -p ~/.ssh/sockets

<font color="red">注意：密码区分中文和英文</font>

解决需要在终端上重复输入密码:

使用ssh的RAS进行免认证.（将本机上的rsa和rsa.pub文件拷贝到远程机上）

```shell
$ ssh-copy-id -i id_rsa-remote-ssh.pub 192.168.0.8
```

该功能对32为的远程机器进行连接