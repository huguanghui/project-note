[TOC]

# 链接

[易百纳](http://www.ebaina.com/)

[海思3516DV300开发环境搭建](https://blog.csdn.net/wssmiss/article/details/102515869)

# 安装交叉编译器的问题

按照海思的用户指南安装arm-hisiv400-linux后，运行命令：arm-hisiv400-linux-gcc -v提示错误：arm-hisiv400-linux-gcc: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory。

这是缺少库文件，按以下命令安装这几个组件：

apt-get install lib32z1 lib32ncurses5
apt-get install lib32stdc++6
