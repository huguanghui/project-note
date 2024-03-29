[TOC]

# SVN和GIT使用

## 修改记录

|    日期    |   描述   | 版本  |  作者  | 审核 |
| :--------: | :------: | :---: | :----: | :--: |
| 2019-04-07 | 初始版本 | 1.0.0 | 胡光辉 |      |
|            |          |       |        |      |
|            |          |       |        |      |

[visualsvn入门文档](https://www.visualsvn.com/server/getting-started/)

## SVN

### svn status的状态显示

- A 已添加
- D 已删除
- U 已更新
- C 合并冲突
- G 合并成功
- E 已存在
- R 已替换

### 检出

```shell
svn checkout svn路径
```

### 多行上传

```shell
# svn多行上传
$ svn commit -m $'1.测试;\n2.上传文件;\n3.完善注释;\n'
```

### 更新到指定版本

```shell
$svn update -r 200 test.php
```

### 版本回退

#### 版本未提交

```shell
# 回退文件
$ svn revert 文件名
# 取消目录
$ svn revert --depth=infinity 目录名
或
$ svn revert -R 目录
```

#### 版本已提交

> 将版本4回退到版本2

![Image 034](assets/Image 034.png)

```shell
# 1. 保证当前的是最新的代码
$ svn update 
# 2. 查看日志确定需要回滚的版本号
$ svn log
# 3. 对比两个版本的差异
$ svn diff -r 4:3 ""
# 4. 回滚版本
$ svn merge -r 4:3 ""
# 5. 确认修改
$ svn diff ""
# 6. 提交
$ svn commit -m $'Revert revision from r4 to r25. 测试版本回退流程.'
```

### 显示一个历史版本中指定文件的内容

```shell
$ svn cat -r 版本号 文件
```

### 在不下载文件到本地目录的情况下来察看目录中的文件

```shell
$ svn list https://192.168.3.125/svn/test_svn
```

### 分支的使用

```shell
# 创建分支
$ svn cp -m "create branch" http://svn_server/xxx_repository/trunk http://svn_server/xxx_repository/branches/br_feature001
# 获取分支
$ svn co http://svn_server/xxx_repository/branches/br_feature001
# 合并主干上的最新代码到分支
$ cd br_feature01
$ svn merge http://svn_server/xxx_repository/trunk 
# 分支合并到主干
$ cd trunk
$ svn merge --reintegrate http://svn_server/xxx_repository/branches/br_feature001
# 合并版本并将合并后的结果应用到现在的分支
$ svn -r 148:149 merge http://svn_server/xxx_repository/trunk
```

### 标签的使用

```shell
# 新建tag
$ svn copy http://svn_server/xxx_repository/trunk http://svn_server/xxx_repository/tags/release-1.0 -m "1.0 released"
```

### 删除分支或tag

```shell
$ svn rm http://svn_server/xxx_repository/branches/br_feature001
$ svn rm http://svn_server/xxx_repository/tags/release-1.0
```

### 使用vimdiff替换原生的1svn diff

新建文件~/.vimdiff

```
1 #!/bin/sh
2 # 配置你喜欢的diff程序路径
3 DIFF="vimdiff"
4 # SVN diff命令会传入两个文件的参数 
5 LEFT=${6}
6 RIGHT=${7}
7 # 拼接成diff命令所需要的命令格式
8 $DIFF $LEFT $RIGHT
```

编辑subversiond的配置文件

```shell
# diff-cmd = diff_program (diff, gdiff, etc.)替换为diff-cmd = /home/user-name/.vimdiff
```

### 特殊使用

```shell
# 修改 svn 的地址
$ svn switch --relocate http://192.168.1.4/svn/zview_4sdi_dvr/firmware/projects_2018/07_AHB8308HIB_AiStick/zwsdk http://192.168.250.4/svn/zview_4sdi_dvr/firmware/projects_2018/07_AHB8308HIB_AiStick/zwsdk
```



## GIT

### 已修改的版本回滚

### 当前目录切换到历史版本

### git status 中文路径显示八进制数字

> 解决办法: git 配置文件 core.quotepath 项设置为 false

### .git文件过大

 现象: 之前误上传了大文件到git服务器后, git的历史记录中就对这个文件做了备份.

 解决办法: 

[参考](https://blog.csdn.net/lai1170137052/article/details/107009414/)

### 新建分支

```shell
$ git branch --track [branch] [remote-branch]
```

### 添加子仓库

```shell
$ git submodule add https://github.com/chaconinc/DbConnector 路径
# 下载带有子仓库的仓库
$ git clone --recurse-submodules [git路径]
$ git submodule update --init --recursive
```



## 提交规范

> 采用比较流行的约定式提交规范,  受 Angular提交准则启发

### 格式

```
<type>(<scope>): <subject>
// 空一行
<body>
// 空一行
<footer> 
```

### type 类型

```
# 主要type
feat:     增加新功能
fix:      修复bug

# 特殊type
docs:     只改动了文档相关的内容
style:    不影响代码含义的改动，例如去掉空格、改变缩进、增删分号
build:    构造工具的或者外部依赖的改动，例如webpack，npm
refactor: 代码重构时使用
revert:   执行git revert打印的message

# 暂不使用type
test:     添加测试或者修改现有测试
perf:     提高性能的改动
ci:       与CI（持续集成服务）有关的改动
chore:    不修改src或者test的其余修改，例如构建过程或辅助工具的变动
```

注意: 当一次改动包括`主要type`与`特殊type`时，统一采用主要type

路径代理

> git config --global -e

```ini
[url "https://hub.fastgit.org/"]
	insteadOf = https://github.com/
[user]
	name = huguanghui
	email = 522146829@qq.com
```

配置git编辑器

```shell
git config --global core.editor lvim
```

删除远程,不删除本地

```shell
git rm -r --cached 文件/文件夹名
```

```PersonToken
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
```

pull冲突合并
```shell
# 链表显示
$ git stash list
# 保存
$ git stash save 1
# 应用
$ git stash apply  stash@{1}
# 删除
$ git stash drop stash@{1}
```

