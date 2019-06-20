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
|            |                     |

## 配置

| 描述     | 路径          |
| -------- | ------------- |
| 配置文件 | ~/.vimrc      |
| 插件     | ~/.vim/bundle |

### 配置文件项

```shell

```

## 插件

### 插件管理器

> 主流的插件管理器分为 vundle 和 vim-plug

[vundle 插件地址](https://github.com/VundleVim/Vundle.vim)

```shell
# 安装
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
# 配置插件(将下面这一段放到 vimrc 的顶部)
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```



## airline插件