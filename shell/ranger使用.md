[TOC]

# ranger 使用

## 基础

```shell
# 创建配置文件
$ ranger --copy-config=all
```

## 使用

| 功能                 | 按键 |
| -------------------- | ---- |
| 显示隐藏文件和文件夹 | zh   |
| 进入当前终端目录     | S    |
| 执行 shell 命令      | s    |
|                      |      |

## 自定义快捷键

```shell
# 将 DD 按键映射为移除到垃圾桶
map DD shell mv %s ~/.Trash
```

