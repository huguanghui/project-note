[TOC]

## 安装

> 当前文档介绍最方便的APT方式进行安装

### graphviz

```shell
$ sudo apt-get install graphviz
```

### doxygen

```shell
$ sudo apt-get install doxygen
```

## 将latex生成pdf中文

```shell
$ sudo apt-get install texlive-full
$ sudo apt-get install latex-cjk-chinese*
$ sudo apt-get install cjk-latex
```

#### 替换脚本

```shell
#!/usr/bin/env bash

sed -i -e 's,begin{document},usepackage{CJKutf8}\n\\begin{document}\n\\begin{CJK}{UTF8}{gbsn},' out/latex/refman.tex
sed -i -e 's,end{document},end{CJK}\n\\end{document},' out/latex/refman.tex
cd out/latex/; make
```

