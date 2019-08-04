[TOC]

## opencv

> 跨平台计算机视觉库.轻量级而且高效.由c++语言编写, 主要接口是c++, 也保留了大量c语言接口.

### linux 开发环境搭建

[OpenCV](https://opencv.org/releases/)

编译 OpenCV

```shell
# 下载源代码
$ cd ~/<my_working_directory>
$ git clone https://github.com/opencv/opencv.git
$ git clone https://github.com/opencv/opencv_contrib.git
# 创建保持编译代码目录
cd ~/opencv
mkdir build
cd build
$ cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local -DOPENCV_GENERATE_PKGCONFIG=ON
# 编译
$ make -j8
# 安装目录
$ sudo make install
```

pkg-config的使用

```shell
export PKG_CONFIG_PATH=/usr/local/库名字/lib/pkgconfig:$PKG_CONFIG_PATH
```

ldconfig的使用

```shell
# 修改系统文件/etc/ld.so.conf，添加路径
$ ldconfig
```

生成 doxygen 文档

[文档](https://docs.opencv.org/master/d4/db1/tutorial_documentation.html)

```shell
# 生成文档
$ yay -S doxygen
$ mkdir doc
$ cmake -DBUILD_DOCS=ON ../opencv-4.1.1
$ make -j8 doxygen
```



## CUDA

