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
| 获取当前绝对路径     |      |

## 自定义快捷键

```shell
# 将 DD 按键映射为移除到垃圾桶
map DD shell mv %s ~/.Trash
```

## 自动挂载U盘

```shell
$sudo apt-get install usbmount
$sudo vim /etc/usbmount/usbmount.conf
在MOUNTOPTIONS那行添加user即可使普通用户也对挂载的U盘拥有写权限, 如下: MOUNTOPTIOS="rw,user,noatime,nodiratime"
```

