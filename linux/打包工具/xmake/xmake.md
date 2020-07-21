## Xmake

## 链接

[xmake官网

](https://xmake.io/#/zh-cn/getting_started)

## xmake的静态编译

```lua
add_ldflags("-static")
```

## 创建空项目

```shell
xmake create -l c -P ./hello
```

## 生成compile_commands

```
xmake project -k compile_commands
```

