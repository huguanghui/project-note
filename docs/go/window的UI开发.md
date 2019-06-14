[TOC]

# window的UI开发

## 修改记录

|    日期    | 描述 | 版本  |  作者  | 审核 |
| :--------: | :--: | :---: | :----: | :--: |
| 2019-06-14 | 创建 | 0.0.1 | 胡光辉 |      |

## 编写目的

> 使用 Go 语言开发桌面GUI程序.

- 掌握 Go 的基础编程
- 制作一个提高工作效率的工具

## 方案分析

### GUI库的选择

|              名称              |      特性       |
| :----------------------------: | :-------------: |
|     github.com/andlabs/ui      |   跨平台ui库    |
|   github.com/salviati/go-qt5   |   QT5的GO绑定   |
| github.com/conformal/gotk3/gtk |   GTK的GO绑定   |
|      github.com/lxn/walk       | Window平台GUI库 |

## 框架介绍

### a. 选择 walk 作为GUI库.

