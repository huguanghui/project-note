[TOC]

# vim的使用

## 链接

[删除相关](https://www.douban.com/note/319225435/)

[复制剪切和粘贴命令](https://www.cnblogs.com/maowang1991/p/3371640.html)

[vim配置参考](https://github.com/consen/dotfiles/blob/master/vim/vimrc)

[vim插件集合](https://vimawesome.com/plugin/youcompleteme)

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
# vi 的最流行的加强版。它在 vi 的基础上增加了很多功能，但就不与 vi 完全兼容了
# 让 vim 关闭所有扩展的功能，尽量模拟 vi 的行为
set compatible
# 关闭兼容模式 (推荐)
set nocompatible
" 设置vim的历史记录条数
set history=2048
" 当外部被修改自动读
set autoread
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

## vim-airline 显示风格插件

[vim-airline](https://github.com/vim-airline/vim-airline)

```shell
Plug 'vim-airline/vim-airline'
```



### YouCompleteMe 自动代码补全插件

[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)

```shell
# 使用 vim-plug安装
Plug 'Valloric/YouCompleteMe'
# 安装
$ cd ~/.vim/bundle/YouCompleteMe
# 下载安装最新的版本libclang
$ apt-get install llvm-3.9 clang-3.9 libclang-3.9-dev libboost-all-dev
```

### 编译ycm_core库(需要安装cmake和python3-dev)

```shell
$ ./install.py --clang-completer
# 配置
$ cp ~/.vim/plugged/YouCompleteMe/third_party/ycmd/examples/.ycm_extra_conf.py ~/.vim/
# 添加vim配置
let g:ycm_server_python_interpreter='/usr/bin/python'
let g:ycm_global_ycm_extra_conf='~/.vim/.ycm_extra_conf.py'
```

### 使用

```shell
# 匹配选择
tab键
# 头文件匹配

```



### gtags 使用

```shell
Plug 'vim-scripts/gtags.vim'
# ctags生成
$ ctags -R -f .tags
# 命令使用
1. ctrl +] // 跟踪
2. ctrl +t或+o //返回
3.:TlistToggle显示索引表
4. ctrl+w w切换视图
```

