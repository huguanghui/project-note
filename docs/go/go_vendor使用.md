[TOC]

## vendor使用

### 安装

> 如果是go1.5，需要环境变量GO15VENDOREXPERIMENT=1，go1.6以上默认开启了这个功能
>
> go get -u github.com/kardianos/govendor

### 使用

#### 初始化

```shell
# 初始化
$ govendor init
```

#### 拉取包

```shell
# 拉取包
$ govendor sync
# 从远程拉取包到vendor下并记录进vendor.json，gopath目录下不会有拉下来的包
$ govendor fetch [包链接，如：github.com/BurntSushi/toml]
# 相当于go get,并复制包到vendor目录下
$ govendor get [包链接，如：github.com/BurntSushi/toml]
```

#### 添加包

```shell
# 添加包会同时在json文件中记录
$ govendor add +external(+e)
# 把项目中的包添加到vendor目录下 必须vendor目录下没有
$ govendor add +local(+l)
# 把标准库的包添加到vendor目录下 必须vendor目录下没有，且vendor.json中没有记录这个包的时候才会添加
$ govendor add +std(+s)
# 把主程序包（main包）添加到vendor目录下 必须vendor目录下没有
$ govendor add +program(+p)
# 把指定包添加进vendor目录 vendor目录下已存在会报错
$ govendor add [包链接，如：github.com/BurntSushi/toml]
# 添加所有的包，包括gopath、go标准库、项目中的包 gopath和标准库下的包必须是被项目或者项目中引用到的包引用的才会添加
$ govendor add +all(+a)
```

#### 删除包

```shell
# 移除项目中的包
$ govendor remove +local(+l)
# 移除未被项目引用的包
$ govendor remove +unused(+u)
# 移除指定包
$ govendor remove [包链接，如：github.com/BurntSushi/toml]
```

#### 其他操作

```shell
# 列出vendor下所有的包
$ govendor list
# 列出应用该包的包
$ govendor list -v [包链名，如：fmt、github.com/BurntSushi/toml]
```



### 依赖包的解决方案

- 当前包下的vendor目录
- 向上级目录查找,直到src下的vendor目录
- 在GOPATH查找依赖包
- 在GOROOT目录下查找

### 注意事项

- 库工程中,不应该在自己的版本中存储外部的包在vendor中
- 应用中,只有vendor目录在代码库一级目录