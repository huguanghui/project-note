[TOC]

# cscope + ctags的使用

## 编写目的

> 熟悉 cscope 和 ctags的单独使用逻辑和独立使用逻辑, 为进一步使用gtags做准备

## 使用

### cscope

```shell
$ find . -name "*.c" -o -name "*.h" -o -name "*.cpp" > cscope.files
$ cscope -Rbkq -i cscope.files
```

| 选项 |                         描述                          |
| :--: | :---------------------------------------------------: |
|  -R  |                      递归子目录                       |
|  -b  |            只生成索引文件不进入cscope界面             |
|  -q  | 生成cscope.in.out和cscope.po.out,加快cscope的检索速度 |
|  -k  |       在生成检索文件时, 不搜索/usr/include目录        |
|  -i  |          当文件名不是cscope.files时,指定列表          |
|      |                                                       |

### ctags

```shell
$ ctags -R
```

