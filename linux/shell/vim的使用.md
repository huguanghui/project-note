[TOC]

# vim的使用

## 链接

[删除相关](https://www.douban.com/note/319225435/)

[复制剪切和粘贴命令](https://www.cnblogs.com/maowang1991/p/3371640.html)

[vim配置参考](https://github.com/consen/dotfiles/blob/master/vim/vimrc)

[vim插件集合](https://vimawesome.com/plugin/youcompleteme)

[vim的c++开发环境](https://juejin.im/post/5cdc396af265da03576ee968)

[C/C++环境搭建](http://www.skywind.me/blog/archives/2084)

[vim本地配置](https://github.com/thinca/vim-localrc)

## 更新

```shell
$ sudo add-apt-repository ppa:jonathonf/vim
$ sudo apt-get update
$ sudo apt-get install vim
```

## 常用命令

```shell
[operate][count][action]
```

| 描述               | 按键                                                   |
| ------------------ | ------------------------------------------------------ |
| 移动               | h-左 l-右 j-下 k-上                                    |
| 删除到行尾         | d$或D                                                  |
| 复制到行尾         | y$                                                     |
| 行尾编辑           | shift+a                                                |
| 行首编辑           | shift+i                                                |
| 上一行编辑         | shift+o                                                |
| 下一行编辑         | o                                                      |
| 垂直分屏           | :sp                                                    |
| 水平分屏           | :vsp                                                   |
| 选中当前位置到行尾 | v$                                                     |
| 向后跳转           | f[word]                                                |
| 向前跳转           |                                                        |
| 折叠               | zf - 创建<br />zo - 打开<br />zc - 关闭<br />zd - 删除 |

## 配置

| 描述     | 路径          |
| -------- | ------------- |
| 配置文件 | ~/.vimrc      |
| 插件     | ~/.vim/bundle |

### 配置文件项

```shell
​```shell
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

### vim-airline 显示风格插件

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

#### 编译ycm_core库(需要安装cmake和python3-dev,python2.7-dev)

```shell
$  ./install.py --clang-completer --go-completer
# 安装 ycmd 中的tool
[submodule "third_party/go/src/golang.org/x/tools"]
     path = third_party/go/src/golang.org/x/tools
     url = https://github.com/golang/tools
     ignore = dirty
# 配置
$ cp ~/.vim/plugged/YouCompleteMe/third_party/ycmd/examples/.ycm_extra_conf.py ~/.vim/
# 添加vim配置
let g:ycm_server_python_interpreter='/usr/bin/python'
let g:ycm_global_ycm_extra_conf='~/.vim/.ycm_extra_conf.py'
# 本地工程的配置
# 将 .ycm_extra_conf.py 拷贝到工程主目录
# 取消每次打开文件提示是否载入 YCM 配置文件
let g:ycm_confirm_extra_conf= 0
" 跳转快捷键
nnoremap <c-k> :YcmCompleter GoToDeclaration<CR>|
nnoremap <c-h> :YcmCompleter GoToDefinition<CR>| 
nnoremap <c-j> :YcmCompleter GoToDefinitionElseDeclaration<CR>|
" 停止提示是否载入本地ycm_extra_conf文件
let g:ycm_confirm_extra_conf = 0
" 语法关键字补全
let g:ycm_seed_identifiers_with_syntax = 1
" 开启 YCM 基于标签引擎
let g:ycm_collect_identifiers_from_tags_files = 1
" 从第2个键入字符就开始罗列匹配项
let g:ycm_min_num_of_chars_for_completion=2
" 在注释输入中也能补全
let g:ycm_complete_in_comments = 1
" 在字符串输入中也能补全
let g:ycm_complete_in_strings = 1
" 注释和字符串中的文字也会被收入补全
let g:ycm_collect_identifiers_from_comments_and_strings = 1
" 弹出列表时选择第1项的快捷键(默认为<TAB>和<Down>)
let g:ycm_key_list_select_completion = ['<C-n>', '<Down>']
" 弹出列表时选择前1项的快捷键(默认为<S-TAB>和<UP>)
let g:ycm_key_list_previous_completion = ['<C-p>', '<Up>']
" 主动补全, 默认为<C-Space>
"let g:ycm_key_invoke_completion = ['<C-Space>']
" 停止显示补全列表(防止列表影响视野), 可以按<C-Space>重新弹出
"let g:ycm_key_list_stop_completion = ['<C-y>']
```

```shell
 13     ctypes.cdll.LoadLibrary( libclang_path )
 14   File "/usr/lib/python2.7/ctypes/__init__.py", line 440, in LoadLibrary
 15     return self._dlltype(name)
 16   File "/usr/lib/python2.7/ctypes/__init__.py", line 362, in __init__
 17     self._handle = _dlopen(self._name, mode)
 18 OSError: /root/.vim/plugged/YouCompleteMe/third_party/ycmd/third_party/clang/lib/libclang.so.8: wrong ELF class: ELFCLASS64 
```

#### 使用

```shell
# 匹配选择
tab键
# 头文件匹配
```

#### 进阶使用

使用 Plug 中的 on 延迟加载

```
# on 为空，后面手动加载
Plug '~/YouCompleteMe', {'on': []}
augroup load_ycm
    autocmd!
    "延迟加载，在 insert 模式手动加载插件
    autocmd InsertEnter * call plug#load('YouCompleteMe') | autocmd! load_ycm
augroup END
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

### 多文件操作

```

```

### fzf 使用

[博客](https://zhuanlan.zhihu.com/p/41859976)

### ale - 语法检测插件

[github](https://github.com/dense-analysis/ale)

[博客](https://blog.csdn.net/demorngel/article/details/69052789)
[博客](https://segmentfault.com/a/1190000016405629)

## python环境

## markdown 插件

[markdown-syntax](https://vimawesome.com/plugin/markdown-syntax)

[vim+markdown](https://zhuanlan.zhihu.com/p/84773275)

## editorconfig 插件

> 统一编码格式规范

[editrconfig](https://vimawesome.com/plugin/editorconfig-vim)

```shell
Plug 'editorconfig/editorconfig-vim'
let g:EditorConfig_exclude_patterns = ['fugitive://.\*', 'scp://.\*']
```

## NeoComplete

> 它通过在当前缓冲区中维护关键字的缓存来提供关键字补全.极易定制, 比内嵌补全具有更多功能.

如果你使用 neovim 或 vim8+, 你应该选择[deoplete](https://github.com/Shougo/deoplete.nvim)

## Deoplete

> dark powered neo-completion 的缩写.在 neovim/vim8 的基础上进行扩展和异步补全框架.deoplete 默认通过 complete 进行补全.

```shell
export PYTHONPATH=/home/hgh/.local/lib/python3.7/site-packages
```

## Snippets

### coc-snippets

```shell
#vim添加coc引擎
Plug 'neoclide/coc.nvim', {'branch': 'release'}
#安装coc-snippets
CocInstall coc-snippets
```

### vim-snippets

#### 问题

#### 使用vim自动识别编码格式文档

#### 检索模型

#### ultisnips的使用

```shell
# 引擎
Plug 'SirVer/ultisnips'
# 代码块集合
Plug 'honza/vim-snippets'
```

## 使用vim快速编辑markdown文档

## easymotion

### 链接

[github](https://github.com/easymotion/vim-easymotion)

### 安装

```shell
Plug 'easymotion/vim-easymotion'
```

### 使用

## vimdiff

### 使用

|    命令     |          描述          |
| :---------: | :--------------------: |
|     ]c      |   跳转到下一个diff点   |
|     [c      |   跳转到上一个diff点   |
|     zo      |        打开折叠        |
|     zc      |        关闭折叠        |
|     dp      | 差异同步到另一个文件中 |
|     do      | 差异同步到本一个文件中 |
| :diffupdate |        刷新页面        |

## vimspector

### 链接

[github](https://github.com/puremourning/vimspector)

```shell
Plug 'puremourning/vimspector', {'do': './install_gadget.py --enable-c --enable-python --enable-go --enable-bash'}

" ===
" === vimspector
" ===
let g:vimspector_enable_mappings = 'HUMAN'
function! s:read_template_into_buffer(template)
	" has to be a function to avoid the extra space fzf#run insers otherwise
	execute '0r ~/.config/nvim/sample_vimspector_json/'.a:template
endfunction
command! -bang -nargs=* LoadVimSpectorJsonTemplate call fzf#run({
			\   'source': 'ls -1 ~/.config/nvim/sample_vimspector_json',
			\   'down': 20,
			\   'sink': function('<sid>read_template_into_buffer')
			\ })
noremap <leader>vs :tabe .vimspector.json<CR>:LoadVimSpectorJsonTemplate<CR>
sign define vimspectorBP text=☛ texthl=Normal
sign define vimspectorBPDisabled text=☞ texthl=Normal
sign define vimspectorPC text=🔶 texthl=SpellBad
```

