[TOC]

# uiresImporter 使用

## 设计目标

>SOUI 目前没有提供 UI 编辑器，所有的 XML 都需要手写，图片很多的文件时导入是一个很麻烦又容易出错的工作



## BAT 脚本

```bat
rem 使用 uiresImporter 来自动导入资源到 uires.idx 及 values\skin.xml.
rem -p 中指定 uires 目录。
rem -s 中指定需要在 uires.idx 中自动更新的文件夹。存在多个目录时应该使用"a|b|c"这样的形式
分割，并使用引号。
rem -i 参数中指定的图片支持自动生成 skin，自动生成 skin 只支持 imglist,imgframe 两种，不
支持的图片放到其它目录，如示例中的滚动条皮肤。
rem -b yes 自动备份原有 XML。no 不备份。
rem -c yes 皮肤默认支持着色处理，no 默认禁止着色。
%SOUI3PATH%\tools\uiresImporter.exe -p uires -s "abc" -i image -b yes -c no
```

