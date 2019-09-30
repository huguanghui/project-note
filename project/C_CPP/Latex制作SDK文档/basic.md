[TOC]

## 环境搭建

[tex live](https://www.tug.org/texlive/) - LaTex布局

latexmk - 编译LaTeX工程

[ChkTeX](http://www.nongnu.org/chktex/) - 检测LaTeX语法

[latexindent.pl](https://github.com/cmhughes/latexindent.pl) - 格式化LaTeX

## 基础理论

### TeX 引擎

> latex, pdflatex, lualatex, xelatex

### 文档包族

#### 1.类型和选项

#### 2.扩展包

2.1 路径

```shell
$ /usr/local/texlive/2019/texmf-dist/tex/latex
```

2.2 安装方式

2.2.1 傻瓜式安装

> 将*.cls或*.sty格式文件

2.2.2 自动安装

```shell
$ tlmgr install <package1> <package2> ...
$ tlmgr remove <package1> <package2> ...
```

2.2.3 手动安装

> 参考[Latex之安装宏包](https://blog.csdn.net/memray/article/details/45248259)

#### 3.类和包的使用

```shell
# 查看包名的信息
$ tlmgr info --list diagbox
```



### 编辑风格

## 使用

### vscode remote-ssh使用Latex环境

### 中文支持

### 封面布局

### 目录制作

### 表格