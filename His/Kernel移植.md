[TOC]

# Kernel移植

## 环境描述

- hi3516DV300
- Hi3516CV500_SDK_V2.0.1.0.tgz

## 烧写 kernel

```shell
hisilion# mw.b 0x82000000 0xff 0x400000
hisilion# tftp 0x82000000 uImage_hi3516dv300
hisilion# sf probe 0;sf erase 0x100000 0x400000;sf write 0x82000000 0x100000 0x400000
```

