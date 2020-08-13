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
# 设置archlinuxcn源
# 更新源列表
$ sudo pacman-mirrors -g
# 更新系统
$ sudo pacman -Syyu
```

### 安装搜狗输入法

```shell
$ sudo pacman -S fcitx
$ sudo pacman -S fcitx-im
$ sudo pacman -S fcitx-configtool
$ sudo pacman -S fcitx-sogoupinyin
# 搜狗输入法异常！请删除.config/SogouPY 并重启
# sogou-qimpanel 查看是否缺少库
$ sudo pacman -S fcitx-qt4
```

### 安装 google 浏览器

```shell
$ sudo pacman -S google-chrome
```

### 安装录屏软件 - simplescreenrecorder

```shell
$ 
sudo pacman -S simplescreenrecorder
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
$ 配置文件目录(~/.config/i3/config)
# 退出i3
$ mod + shift + e
```

```shell
#polybar配置
exec --no-startup-id $HOME/.config/polybar/launch.sh
```

#### 扩展屏安装

> exec --no-startup-id xrandr --output HDMI1 --auto --left-of eDP1

### 安装终端 - alacritty

```shell
$ sudo pacman -S alacritty
# 配置透明度为0.6, 执行compton
```

### 安装 - dmenu

```shell
$ sudo pacman -S dmenu
```

### 安装 - wechat

```shell
$ yay -S deepin-wechat
```

### 安装 - Tim

```shell
$ yay -S deepin-wine-tim
```



## feh - 壁纸管理器

```shell
$ sudo pacman -S feh
```

## variety

```shell
$ sudo pacman -S variety
```

## compton

```
$ sudo pacman -S compton
```



## 安装 - samba

```shell
$ sudo pacman -S samba
$ wget "https://git.samba.org/samba.git/?p=samba.git;a=blob_plain;f=examples/smb.conf.default;hb=HEAD" -O /etc/samba/smb.conf
# 添加
#[linux]
#path=/home/linux
#valid users=linux
#public=yes
#writable=yes
# 创建 samba 用户
$ sudo systemctl restart smb.service
$ sudo systemctl restart nmb.service
或 sudo systemctl restart smb nmb
# 设为开机启动
$ sudo systemctl enable smb.service
$ sudo systemctl enable nmb.service
或 sudo systemctl enable smb nmb
#手动挂载
#mount -t cifs -o username=用户名,password=密码  //ip地址/共享文件夹名 挂载点
mkdir test
mount -t cifs -o username=user1,password=you_password //service_ip/test ./test  #成功
#smbmount -o username=用户名,password=密码  //ip地址/共享文件夹名 挂载点   #未测试
```

## 安装 - tftp

```shell
$ sudo pacman -S tftp-hpa
$ 配置文件(/etc/conf.d/tftpd),改为“TFTPD_ARGS="-l -s /home/hgh/tftp_dir"”
$ systemctl start tftpd.service
$ systemctl enable tftpd.service
# 测试

```

## GNOME的快捷建

```shell
# 应用搜索ddddd
$ win键 或 alt+F1
```

## Polybar的使用

```shell
# 安装(根据网上推荐直接使用 aur 方式安装)
$ yaoaur -S polybar
# 创建默认配置文件
$ cp /usr/share/doc/polybar/config ~/.config/polybar/config
# 执行启动命令i3启动(具体见github的template目录)
$ ~/.config/polybar/launch.sh
```

## 安装 deepin 录屏软件

```shell
$ sudo pacman -S deepin-screen-recorder
```

## 终端信息显示

```shell
$ sudo pacman -S neofetch
```

## Manjaro 安装字体

```shell
# 安装地址
路径: /usr/share/fonts/TTF
# 刷新字体
$ fc-cache -fv
```

## nfs 服务

```shell
pacman -S nfs-utils
将 nfs-server 加入/etc/rc.conf 中的 daemon 项。
修改/etc/exports,在其中加入:
/home/chinsung/workspace/test 192.168.0.0/255.255.255.0(rw,no_root_squash,sync)
即共享本机上的/home/chinsung/workspace/test 目录,192.168.0.0/255.255.255.0 网段中的计
算机有访问权限,文件执行权限为 rw,no_root_squash,sync。
在客户机中执行
mount -o rw,nolock 192.168.0.101:/home/chinsung/workspace/test ./test
即将远程主机 192.168.0.101 上的 home/chinsung/workspace/test 目录 mount 到./test 目录中
```

## 修改默认文本编辑器

```shell
$ echo export EDITOR=/usr/bin/vim >> ~/.bashrc 
```

## 安装微信,迅雷,网易云音乐,百度网盘

https://www.jianshu.com/p/e4d2c3698ec9