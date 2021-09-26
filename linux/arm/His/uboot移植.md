[TOC]

# uboot移植

## 环境描述

- his3516DV300
- Hi3516CV500_SDK_V2.0.1.0.tgz

## 编译

```shell
# 路径Hi3516CV500_SDK_V2.0.1.0/osdrv/opensource/uboot/u-boot-2016.11
# 配置编译环境
$ make ARCH=arm CROSS_COMPILE=arm-himix200-linux- hi3516dv300_config
# 编译uboot, 生成u-boot.bin
$ make ARCH=arm CROSS_COMPILE=arm-himix200-linux- -j 20
# 配置DDR寄存器
# 配置管脚复用
# 生成最终使用的uboot镜像
# 使用hiregbin生成reg_info.bin
$ ./hiregbin ./Hi3516dv300.xlsm ./reg.bin
# 将reg_info.bin拷贝到uboot源码改为.reg
$ make ARCH=arm CROSS_COMPILE=arm-himix200-linux- u-boot-z.bin
```

## Uboot使用

```shell
hisilion#setenv serverip 192.168.3.16
hisilion#setenv ipaddr 192.168.3.22
hisilion#setenv netmask 255.255.255.0
hisilion#setenv gatewayip 192.168.3.1
hisilion#saveenv
# 使用tftp烧录uboot <ddr_addr> 0x82000000
hisilion# mw.b <ddr_addr> ff 0x100000  /*对内存初始化*/
hisilion# tftp <ddr_addr> u-boot-hi3516cv500.bin /*tftp下载到内存*/
hisilion# sf probe 0   /*探测并初始化SPI-Nor flash*/
hisilion# sf erase 0x0 0x100000  /*擦除1M大小*/
hisilion# sf write <ddr_addr> 0x0 0x100000 /*从内存写入SPI-Nor flash*/
```

## Uboot启动项

```shell
U-Boot 2016.11 (Jan 01 2020 - 15:55:30 +0800)hi3516dv300

Relocation Offset is: 0f6c3000
Relocating to 8fec3000, new gd at 8fe22ef0, sp at 8fe22ed0
SPI Nor:  Check Flash Memory Controller v100 ... Found
SPI Nor ID Table Version 1.0
SPI Nor(cs 0) ID: 0xef 0x40 0x18
Block:64KB Chip:16MB Name:"W25Q128(B/F)V"
SPI Nor total size: 16MB
NAND:  0 MiB
MMC:
In:    serial
Out:   serial
Err:   serial
Net:   eth0
Hit any key to stop autoboot:  0
hisilicon # <INTERRUPT>
hisilicon # <INTERRUPT>
hisilicon # <INTERRUPT>
hisilicon # printenv
arch=arm
baudrate=115200
board=hi3516dv300
board_name=hi3516dv300
bootargs=mem=128M console=ttyAMA0,115200 root=/dev/mtdblock2 rootfstype=jffs2 rw mtdparts=hi_sfc:1M(boot),4M(kernel),11M(rootfs)
bootcmd=sf probe 0;sf read 0x81000000 0x100000 0x400000;bootm 0x81000000
bootdelay=2
cpu=armv7
ethact=eth0
ethaddr=82:be:d4:86:e6:74
fileaddr=82000000
filesize=4a360
gatewayip=192.168.3.1
ipaddr=192.168.3.22
netmask=255.255.255.0
serverip=192.168.3.16
soc=hi3516dv300
stderr=serial
stdin=serial
stdout=serial
vendor=hisilicon
verify=n

Environment size: 575/262140 bytes
hisilicon #
```

## 文档归档

### lds链接脚本详解

[lds链接脚本](https://www.cnblogs.com/li-hao/p/4107964.html)

### ARM v7-A体系结构文档

[文档](https://static.docs.arm.com/ddi0406/cd/DDI0406C_d_armv7ar_arm.pdf?_ga=2.184636073.1655147749.1578112337-302947942.1578112337)

```shell
《ARM体系结构与编程》杜春雷
链接：https://pan.baidu.com/s/1c1Kf2fQ 密码：cxnu
```

### Uboot中start.S源码的指令级的详尽解析

[start.S源码解析](https://www.crifan.com/files/doc/docbook/uboot_starts_analysis/release/html/uboot_starts_analysis.html#fg.arm_3_tie_pipeline_example)

### ARM指令详解

[ARM指令详解](https://blog.csdn.net/mickey35/article/details/82011449)

## uboot启动流程

### 汇编部分

#### 1. u-boot.lds

```c
_start
```

#### 2. start.S

```c
reset -> save_boot_params
```



### C部分

```c
CONFIG_BOOTCOMMAND
```

```
setenv bootargs "mem=128M console=ttyAMA0,115200 root=/dev/mtdblock2 rootfstype=jffs2 rw mtdparts=hi_sfc:1M(boot),4M(kernel),11M(rootfs)"
```

```
arch=arm
baudrate=115200
board=hi3516dv300
board_name=hi3516dv300
bootargs=mem=128M console=ttyAMA0,115200 root=/dev/mtdblock2 rootfstype=squashfs rw mtdparts=hi_sfc:1M(boot),4M(kernel),3584K(rootfs),2M(ko),4608K(app),512K(config),512K(custom)
bootcmd=sf probe 0;sf read 0x80600000 0x100000 0x400000; bootm 0x80600000
bootdelay=2
cpu=armv7
ethact=eth0
ethaddr=1a:ae:46:b8:4f:42
ipaddr=192.168.3.77
serverip=192.168.3.90
soc=hi3516dv300
stderr=serial
stdin=serial
stdout=serial
vendor=hisilicon
verify=n
```

