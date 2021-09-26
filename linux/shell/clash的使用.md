## clash的使用

### clash服务创建

/etc/systemd/system/clash.service

```shell
[Unit]
Description=Clash Daemon

[Service]
ExecStart=/usr/local/bin/clash -d /etc/clash/
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

