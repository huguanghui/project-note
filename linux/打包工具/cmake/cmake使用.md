[TOC]

## Mconf

### 源码地址

[Menuconfig](https://github.com/TheGeorge/menuconfig)

改为静态方式

```shell
# c
set(CMAKE_C_FLAGS "-static ${CMAKE_C_FLAGS}")
# cpp
set(CMAKE_CXX_FLAGS "-static ${CMAKE_CXX_FLAGS}")
```

## CMake编译参数

