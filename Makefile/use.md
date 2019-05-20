[TOC]

## cmake使用

[CMake使用](http://www.cnblogs.com/hgwang/p/9100343.html)

[简介](https://www.cnblogs.com/lidabo/p/7359422.html)

## 使用案例

```cmake
file(GLOB TARGET_PROG_LIST "*/*.cpp")
```

file在CMake中是文件操作命令.[参考](<https://blog.csdn.net/bytxl/article/details/48287499>)

**file(GLOB variable [RELATIVE path] [globbingexpressions]...)**

GLOB会产生一个由所有匹配globbing表达式的文件组成的列表，并将其保存到变量中。Globing表达式与正则表达式类似，但更简单。如果指定了RELATIVE 标记，返回的结果将是与指定的路径相对的路径构成的列表。 (通常不推荐使用GLOB命令来从源码树中收集源文件列表。原因是：如果CMakeLists.txt文件没有改变，即便在该源码树中添加或删除文件，产生的构建系统也不会知道何时该要求CMake重新产生构建文件