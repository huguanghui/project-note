[TOC]

# Merurial搭建

## 源码安装

### 前期准备

- python2.4+
- python-dev
- gcc

对于Mercuial1.3.x或更早的版本,需要 [AsciiDoc](http://www.methods.co.nz/asciidoc/) and [xmlto](https://fedorahosted.org/xmlto/),之后的版本改为需要 libxslt.

对于Mercuial1.4或之后的版本需要Docutils.

## ubuntu安装

> 使用apt进行安装

```shell
$ sudo apt-get install mercurial
```

## 使用

> 应用场景由易到 难来使用mercurial

### 简单的工作流场景

#### 1. 持续的修改日志

**场景**

​	使用mercurial查看提交的修改记录

**操作流程**

 1.配置用户信息

    ```shell
    // 打开~/.hgrc文件添加
    [ui]
    username = huguanghui <522146829@qq.com>
    ```

2.工程操作

空项目建立

```shell
$ hg init project      					# 创建project工程
$ cd project							# 进入project工程
$ echo 'print("Hello")' > hello.py   	# 修改内容
$ hg add								# 添加修改
$ hg commit								# 提交修改
$ hg log  								# 查看修改记录
```

已有项目建立

```shell
$ cd project							# 进入已有项目目录
$ hg init 								# 初始化仓库
$ hg add <file>                         # 添加需要提交的文件
$ hg status								# 查看状态
$ hg diff								# 对比差异
$ hg commit                             # 提交修改
```

复制和移动文件操作

```shell
$ hg cp hello.py copy     				# 文件拷贝
$ hg mv hello.py target					# 文件移动
```

#### 2.非线性历史的独立开发人员

**场景**

假如你是一位使用Mercurial来追踪修改和优化流程的独立开发人员.

- 可能会有回溯操作.
- 完成一部分功能就提交.
- 随时查看修改记录和程序进展

**操作流程**

1.版本回退

```shell
$ hg update 1                       	# 回退到版本1
$ hg identify -n						# 修改对应参数后,添加标识
$ hg update tip							# 更新到最新版本
```

2.解决早期版本中的问题

在早期版本中发现问题的两种解决办法:1.在最新版本中解决提交;2.切换到早期版本中解决(可以让历史版本更干净)

```shell
$ hg update 1              							# 回退到有问题的版本
$ echo 'print("Hello Mercurial")' > hello.py		# 修改问题
$ hg add 
$ hg commit											# 提交修改
$ hg merge 											# 提交合并
$ hg resolve --list									# 列出文件冲突
$ hg resolve conflicting_file						# 手动解决冲突后尝试合并解决
$ hg resolve --mark conflicting_file                # 将固定文件标记为已解决
$ hg commit 										# 解决所有冲突后尝试提交
```

#### 3.分开的功能

**场景**

同一时间同时处理几个功能.

- 创建分支
- 功能开发完毕合并到主干,合并冲突

**操作流程**

1.开发分支功能

```shell
$ hg clone project feature1       					# 克隆分支
$ cd feature										# 进入特性分支
$ hg update 3									 	# 回退到版本3
$ echo 'print("Hello feature1")' > hello.py			# 分支功能开发
$ hg commit -m "Greet feature1"						# 提交修改
$ cd ../project										# 进入主干目录
$ hg incoming ../feature1
$ hg incoming --patch								# 查看差异
$ hg pull ../feature1								# 认可功能, 拉取到主干
$ hg merge											# 提交合并请求
$ hg commit											# 合并上传
```

2.回滚错误

如果你在并行的多个功能分支上,可能会有错误的提交.可以回退版本解决错误.当你在进行另一个提交或拉取时，意识到了一个错误.回滚意味着测试已经写入记录的上次提交.

```shell
$ hg rollback 										# 回滚
$ hg commit -m "Merged Feature 1"					# 提交
```

#### 4.分享改变

**场景**

不再是独立的开发者,将代码分享出去

**操作流程**

1.使用内嵌Web服务器方式

```shell
$ hg serve                               			# 使用内嵌的Web服务器
```

2.通过email发送改变

```shell
$ cd project
$ hg log
$ hg export 3 > change3.diff
$ hg export 4 > change4.diff
```

3.使用一个共享仓库

[BitBucket](http://bitbucket.org/)

### 进阶场景

#### 1.支持

**场景**

当你经常从别人那里拉取代码时,你可能忽略掉一些不好的变化.同样其他人从你那里拉取修改的代码,你就很难摆脱它.在任意的分布式系统中为了彻底解决这个问题,Mercurial提供了一个backout命令.倒退一个改变意味着你通知Mercurial创建一个提交去扭转这个坏的提交.这样你就不会摆脱历史上的错误代码，但你可以从新版本中删除它.

**操作流程**