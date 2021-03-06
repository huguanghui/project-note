[TOC]

# VSCode

## 快捷键

|       功能       |    快捷键    |
| :--------------: | :----------: |
|  打开资源管理器  | ctrl+shift+e |
| 切换侧边栏可见性 |    ctrl+b    |
|     转到文件     |    ctrl+p    |
| 转到文件中的符号 | ctrl+shift+o |



## 包含文件和排除文件使用技巧

./nam, ./src, ./test

## 环境

### 图标

> 使用VSCode Great Icons
>
> 使用Material Icon Theme

### 主题

> 使用Bracket主题插件 Bracket Light Pro
>
> 背景颜色改为 204 232 207 或 #CCE8CF

在插件的配置文件中

将 "editor.background" 和 "editor.lineHighlightBackground" 配置改为 #CCE8CF.

### 高亮选中背景

> highlight-icemode

## 远程开发

> 该插件可以让我们通过SSH，远程设备或虚拟机，WSL，或是在Docker容器使用VSCode远程编辑.

[blog](https://code.visualstudio.com/blogs/2019/05/02/remote-development)

## VSCode中快捷键打开google浏览器

在插件栏中搜索 "open in browser"

选中*.html文件，按 alt + b

## C/C++的开发环境

- C/C++插件
- C/C++ Intellisense插件 + gtags
- [CTags Support](https://github.com/jaydenlin/ctags-support)

## 优化配置

### 去掉打开软件自动打开上次工程

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

[参考链接](https://blog.csdn.net/qq_41554005/article/details/103103443)

```shell
scp %USERPROFILE%\.ssh\id_rsa.pub 192.168.1.41:~/tmp.pub
touch ~/.ssh/authorized_keys
cat ~/tmp.pub >> ~/.ssh/authorized_keys
rm -f ~/tmp.pub
```

使用ssh的RAS进行免认证.（将本机上的rsa和rsa.pub文件拷贝到远程机上）

```shell
$ ssh-copy-id -i id_rsa-remote-ssh.pub 192.168.0.8
```

该功能对32为的远程机器进行连接

#### 监测文件数

##### 修改最大值

```shell
$ cat /proc/sys/fs/inotify/max_user_watches
# 配置/etc/sysctl.conf 新增 fs.inotify.max_user_watches=524288
$ sudo sysctl -p
```

##### 过滤文件

```json
"files.watcherExclude": {
    "**/.git/objects/**": true,
    "**/.git/subtree-cache/**": true,
    "**/node_modules/*/**": true
  }
```

### 远程WSL

#### wsl的重启

```shell
# 管理员模式运行shell
$ net stop LxssManager
$ net start LxssManager
```

## Vim的使用

[vim的使用](https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.md)

### 配置

> 

### c/c++的系统默认include路径配置

```shell
# c++
$ gcc -v -x c++ -E -
# c
$ gcc -v -x c -E -
```

```json
	"C_Cpp.default.systemIncludePath": [
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/../../../../arm-hisiv500-linux-uclibcgnueabi/include/c++/4.9.4",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/../../../../arm-hisiv500-linux-uclibcgnueabi/include/c++/4.9.4/arm-hisiv500-linux-uclibcgnueabi",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/../../../../arm-hisiv500-linux-uclibcgnueabi/include/c++/4.9.4/backward",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/include",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/include-fixed",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../lib/gcc/arm-hisiv500-linux-uclibcgnueabi/4.9.4/../../../../arm-hisiv500-linux-uclibcgnueabi/include",
		"/opt/hisi-linux/x86-arm/arm-hisiv500-linux/bin/../target/usr/include"
	]
```

## 绘制流程图

[博客](https://baijiahao.baidu.com/s?id=1667351591614061966&wfr=spider&for=pc)

### 问题

#### 解决中文乱码问题

## 调试功能

### C/C++调试

#### 方案一

> 使用 tasks.json + launch.json 方式来进行调试

适用场景

> 文件单一, 依赖库少的情况

#### 方案二

> 使用cmake插件进行调试, 调试不了第三方库

#### 方案三

> 使用xmake插件进行调试，调试不了第三方库

使用vscode进行 xmake 调试要注意在 lua 中加入一下配置

```lua
-- add modes: debug and release
add_rules("mode.debug", "mode.release")
```

