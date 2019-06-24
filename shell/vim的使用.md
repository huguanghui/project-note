[TOC]

# vim的使用

## 链接

[删除相关](https://www.douban.com/note/319225435/)

[复制剪切和粘贴命令](https://www.cnblogs.com/maowang1991/p/3371640.html)

## 常用命令

```shell
[operate][count][action]
```

| 描述       | 按键                |
| ---------- | ------------------- |
| 移动       | h-左 l-右 j-下 k-上 |
| 删除到行尾 | d$或D               |
| 复制到行尾 | y$                  |
| 行尾编辑   | shift+a             |
| 行首编辑   | shift+i             |
| 上一行编辑 | shift+o             |
| 下一行编辑 | o                   |
| 垂直分屏   | :sp                 |
| 水平分屏   | :vsp                |
|            |                     |

## 配置

| 描述     | 路径          |
| -------- | ------------- |
| 配置文件 | ~/.vimrc      |
| 插件     | ~/.vim/bundle |

### 配置文件项

```shell
```shell
# 修改换行缩进

```

## 插件

### vim-plug 插件管理器

[vim-plug](https://github.com/junegunn/vim-plug)

```shell
# unix 安装
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### 命令

| Command                             | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| `PlugInstall [name ...] [#threads]` | Install plugins                                              |
| `PlugUpdate [name ...] [#threads]`  | Install or update plugins                                    |
| `PlugClean[!]`                      | Remove unused directories (bang version will clean without prompt) |
| `PlugUpgrade`                       | Upgrade vim-plug itself                                      |
| `PlugStatus`                        | Check the status of plugins                                  |
| `PlugDiff`                          | Examine changes from the previous update and the pending changes |
| `PlugSnapshot[!] [output path]`     | Generate script for restoring the current snapshot of the plugins |

### YouCompleteMe 自动代码补全插件

[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)

```shell
# 使用 vim-plug安装
Plug 'Valloric/YouCompleteMe'
```

