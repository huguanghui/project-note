[TOC]

# 使用QEMU调试kernel

## 修改记录

|    日期    |   描述   | 版本  |  作者  | 审核 |
| :--------: | :------: | :---: | :----: | :--: |
| 2019-10-15 | 初始版本 | 1.0.0 | 胡光辉 |      |

## 编写目的

> 了解kernel的原理和机制

## 相关链接

[从零使用qemu模拟器搭建arm开发环境](https://blog.csdn.net/linyt/article/details/42504975)

[qemu官网](https://www.qemu.org/)

## QEMU源码

```shell
git clone https://gitlab.com/qemu-project/qemu.git
cd qemu
git submodule init
git submodule update --recursive
./configure
make
```

## uboot调试

[gdb安装](https://zhuanlan.zhihu.com/p/134031693)

[u-boot](http://ftp.denx.de/pub/u-boot/)

### 环境

- 虚拟机: vexpress-a9
- uboot版本 u-boot-2017.05

```sh
# uboot编译
$export ARCH=arm  CROSS_COMPILE=arm-linux-gnueabi-  
$make vexpress_ca9x4_defconfig  
$make -j8  
```

```sh
# 虚拟机运行
$ qemu-system-arm -M vexpress-a9 -kernel u-boot -nographic -m 512M -gdb tcp:1234 -S -s
```

```sh
# 启动gdb
arm-none-eabi-gdb
(gdb)  file u-boot  
(gdb)  target remote:1234
```



## kernel源码

```shell
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
```

