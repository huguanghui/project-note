[TOC]

# frp

## 简介

## 搭建

system方式开机启动

```
# 路径 /etc/systemd/system/frpc.service
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
User=nobody
Restart=on-failure
RestartSec=5s
ExecStart=/usr/bin/frps -c /etc/frp/frps.ini

[Install]
WantedBy=multi-user.target
```

