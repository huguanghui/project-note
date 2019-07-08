[TOC]

# Manjaro 系统

## 链接

[Manjaro](https://www.manjaro.cn/)

## Arch, Debian

## 初期配置

### 更换源

```shell
# 选择中国最快的镜像
$ sudo pacman-mirrors -c China
# 更新系统
$ sudo pacman -Syyu
```

### 安装搜狗输入法

```shell
$ sudo pacman -S fcitx
$ sudo pacman -S fcitx-im
$ sudo pacman -S fcitx-configtool
$ sudo pacman -S fcitx-sogoupinyin
# 决搜狗输入法异常！请删除.config/SogouPY 并重启
$ sudo pacman -S fcitx-qt4
```

### 安装 google 浏览器

```shell
$ sudo pacman -S google-chrome
```

### 安装录屏软件 - simplescreenrecorder

```shell
$ sudo pacman -S simplescreenrecorder
```

### 安装按键显示 - screenkey

```shell
$ sudo pacman -S screenkey
```

###  安装编辑器 - vim

```shell
$ sudo pacman -S vim
```

### 安装 fish

```shell
$ sudo pacman -S fish
# 切换 fish
$ chsh -s /usr/bin/fish
# 使用 oh-my fish
$ curl -L https://get.oh-my.fish | fish
# 配置
$ fish_config
# oh-my fish 安装插件
$ omf install
# alias 使用
$ alias c clear
$ funcsave c
```

### 安装 i3

```shell
$ sudo pacman -S i3
# 修改页面大小
# vim ~/.Xresources
Xft.dpi: 200
```

### 安装终端 - alacritty

```shell
$ sudo pacman -S alacritty
```

### 安装 - dmenu

```shell
$ sudo pacman -S dmenu
```

