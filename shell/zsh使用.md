[TOC]

# ZSH使用

> zsh和bash一样,是shell的一种

[oh-my-zsh官网](https://ohmyz.sh/)

[git的oh-my-zsh使用](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git)

[Linux的四大开发利器](https://consen.github.io/2017/02/14/four-linux-development-tools/)

## 安装

```shell
# APT
$ sudo apt-get install zsh
# 设置当前用户使用
$ chsh -s /bin/zsh
```

### 安装oh my zsh

> 安装完成后重启电脑

```shell
# 自动安装
$ wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
# 手动安装
$ git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
$ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

### 配置

> zsh的配置集中在用户当前目录的.zshrc里.

设置别名

```c
alias -s gz='tar -xzvf'
```



### 安装插件

### colored-man-pages

> 让man手册有颜色

#### autojump自动跳转插件

```shell
sudo apt-get install autojump
# 添加到~/.zshrc配置中
// . /usr/share/autojump/autojump.sh
# 生效
source ~/.zshrc
```

#### zsh-syntax-highlighting语法高亮插件

> 可提示命令写错

```shell
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
$ echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

#### zsh-autosuggestions语法历史记录插件

```shell
$ git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
# vim.tiny ~/.zshrc
plugins={
    git
    zsh-autosuggestions
}
# source $ZSH_CUSTOM/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
```

## 更换主题

```shell
# vim ~/.zshrc
# 修改ZSH_THEME参数, 推荐(ys)
```

## 卸载

```shell
# 执行
sudo sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/uninstall.sh)"
# 将/etc/passwd中修改shell的方式.
```

## 使用技巧

- 输入一个命令可以查看之前相关的使用记录
- 补全技巧
- autojump自动跳转功能
- d目录浏览和跳转
- 通配符搜索 
- 使用别名技巧
- 插件和主题更换

### 快捷键

```shell
ctrl + a，移动到行首
ctrl + e，移动到行尾
ctrl + f，前移一个字符
ctrl + b，后移一个字符
ctrl + w，删除光标前面的单词
ctrl + d，删除光标所指的字符
ctrl + k，删除光标至行尾的所有内容
ctrl + u，清空当前行
cmd + r，清空当前屏幕
cmd + ; ，根据历史命令，对当前输入自动补全
cmd + shift + h，自动补全剪贴板历史
cmd + f，查找
enter，上一个匹配结果
shift + enter，下一个匹配结果
```

### vi-mode 的插件使用

[vi-mode 的插件基础教程](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/vi-mode)