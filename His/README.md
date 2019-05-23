[TOC]

# His开发环境

[HI3519V101环境搭建](https://blog.csdn.net/simonforfuture/article/details/78512479)

## C语言标准库

> 目前分为Glibc, uClibc和EGlibc

|  类型  |                             特点                             |
| :----: | :----------------------------------------------------------: |
| Glibc  | 是GNU项（GNU Project）目<br /> 用于桌面级和服务器系统中<br />支持多种平台系统,功能齐全,缺点比较大 |
| uClibc | 设计用于uClinux,<br />主要用于嵌入式<br />因此比较适用于微处理器<br />与glibc在源代码和二进制上完全不兼容<br />不支持内存管理单元 |
| EGlibc | y源代码和二进制兼容于Glibc<br />降低内存占用<br />更多模块可配置<br />提高对交叉编译和交叉测试的支持 |

