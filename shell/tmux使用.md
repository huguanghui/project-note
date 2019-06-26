[TOC]

# tmux

> 终端分屏管理工具.分为三个部分: 会话session, 窗口window, 窗格pane.本文是基于v2.6的版本上测试的.

## 链接

[github仓库](https://github.com/tmux/tmux)

[tmux 速成教程](https://thoughtbot.com/blog/a-tmux-crash-course)

[教程](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

[tmux 的 wiki](https://wiki.archlinux.org/index.php/tmux)

[参考配置](https://github.com/consen/dotfiles)

[oh my tmux](https://github.com/gpakosz/.tmux/blob/master/.tmux.conf)


## 安装

```shell
# ubuntu 上的安装
$ sudo apt-get install tmux
```

## 配置

> tmux 的用户级配置文件的位置~/.tmux.conf

```shell
# set scrollback history to 10000
set -g history-limit 10000

# use PREFIX | to split window horizontally and PREFIX - to split vertically
bind | split-window -h
bind - split-window -v

# hjkl pane traversal
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
# resize panes
bind C-h resize-pane -L 5
bind C-j resize-pane -D 5
bind C-k resize-pane -U 5
bind C-l resize-pane -R 5

# vi copypaste mode
set-window-option -g mode-keys vi
bind-key -Tcopy-mode-vi 'v' send -X begin-selection
bind-key -Tcopy-mode-vi 'V' send -X rectangle-toggle
bind-key -Tcopy-mode-vi 'y' send -X copy-selection

# 修改下边栏显示
set -g status-left "s-#S:w-#I:p-#P #[default]"
set -g status-right "#(whoami)  %Y-%m-%d %H:%M #[default]"
set -g status-left-length 64
set -g status-right-length 64

# colors in vim in tmux
# tmux 1.9 or later, comment this line and start tmux with 'tmux -2'
#set -g terminal-overrides "xterm:colors=256"

set-option -g status-bg colour236
set-option -g status-fg colour185
set-option -g status-attr default

# default window title colors
set-window-option -g window-status-fg colour242
set-window-option -g window-status-bg default

# active window title colors
set-window-option -g window-status-current-fg colour166
set-window-option -g window-status-current-bg default

# pane border
set-option -g pane-active-border-fg colour166
#set-option -g pane-active-border-bg black
set-option -g pane-border-fg colour242
#set-option -g pane-border-bg black

# message text
set-option -g message-bg colour236
set-option -g message-fg colour166

# reload config
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."


# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-resurrect'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

## 使用

> ctrl + b ？ 查看帮助

### 会话

```shell
# 新建
$ tmux new -s session-name
# 断开
$ tmux detach
# 列出会话
$ tmux ls
# 连接会话
$ tmux attach -t session-name
# 退出并保存会话
$ ctrl+b d
# 选择会话
$ ctrl+b s
```

### 窗口

```shell
# 新建
$ ctrl+b c
# 列出所有窗口
$ ctrl+b w
# 切换
$ ctrl+b [0-9]
# 关闭窗口
$ ctrl+b &
```

### 窗格

```shell
# 新建垂直窗格
$ ctrl+b "
$ ctrl+b -
# 新建水平窗格
$ ctrl+b %
$ ctrl+b |
# 删除
$ ctrl+b x
# 切换窗格(不要同时按)
$ ctrl+b 方向键
# 最大化窗格/取消最大窗口
$ ctrl+b z
# 显示窗口序号
$ ctrl+b q
```

### 插件使用

> tmux有个缺点就是无法持久保存session. 使用Tmux-Resurrect插件可以解决这个问题

[tmux 的插件管理器 tpm](https://github.com/tmux-plugins/tpm)

```shell
# 安装
$ git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
# 命令
# a.安装
$ ctrl+b I
# b. 更新
$ ctrl+b U
# c. 卸载没有使用的插件
$ ctrl+B alt+u
```

配置文件中添加

```shell
# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-sensible'

# Other examples:
# set -g @plugin 'github_username/plugin_name'
# set -g @plugin 'git@github.com/user/plugin'
# set -g @plugin 'git@bitbucket.com/user/plugin'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run -b '~/.tmux/plugins/tpm/tpm'
```

#### tmux-resurrect插件的使用

```shell
# 保存
$ ctrl+b ctrl+s
# 恢复
$ ctrl+b ctrl+r
```

