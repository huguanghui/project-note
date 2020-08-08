## Xmake

## 链接

[xmake官网](https://xmake.io/#/zh-cn/getting_started)

## 使用

### xmake的静态编译

```lua
add_ldflags("-static")
```

### 创建空项目

```shell
xmake create -l c -P ./hello
```

### 编译

```shell
xmake build -r [target]
```
$ xmake project -k compile_commands
```

```
$ xmake require --info tbox
```

## tbox的依赖库管理机制

```shell
add_requires("tbox", {debug = is_mode("debug"), config = {object = true}})
```

## 配置

### Linux 的配置项

```shell
# 交叉编译器配置
$ xmake f -p linux --cross=arm-himix100-linux- --sdk=/opt/hisi-linux/x86-arm/arm-himix100-linux -a arm -m debug
# option 配置
```

### Windows  上的配置

```shell
$
```

