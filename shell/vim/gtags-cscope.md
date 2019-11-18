[TOC]

# gtags-cscope的配置

## vim中的配置

```shell
set cscopetag                  " 使用 cscope 作为 tags 命令
set cscopeprg='gtags-cscope'   " 使用 gtags-cscope 代替 cscope
" gtags
let GtagsCscope_Auto_Load = 1
let CtagsCscope_Auto_Map = 1
let GtagsCscope_Quiet = 1
```

|   命令    |                         描述                          |
| :-------: | :---------------------------------------------------: |
|  Ctrl+]   |                        跳转到                         |
|  Ctrl+T   |                         返回                          |
| cs find s |  查找C语言符号，即查找函数名、宏、枚举值等出现的地方  |
| cs find g | 查找函数、宏、枚举等定义的位置，类似ctags所提供的功能 |
| cs find d |                 查找本函数调用的函数                  |
| cs find c |                 查找调用本函数的函数                  |
| cs find t |                   查找指定的字符串                    |
| cs find e |   查找egrep模式，相当于egrep功能，但查找速度快多了    |
| cs find f |           查找并打开文件，类似vim的find功能           |
| cs find i |                 查找包含本文件的文件                  |

