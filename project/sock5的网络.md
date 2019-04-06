[TOC]

## 链接

[轻松在 VPS 搭建 Shadowsocks 翻墙 ](https://www.diycode.cc/topics/738)

## 服务端

### VPS安装ShadowSocks

```shell
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

```
// shadowsocks-go
$/etc/init.d/shadowsocks-go status
```



## 客户端

```shell
sudo sslocal -c /etc/shadowsocks.json &
hgh@hgh-Macmini:~$ cat /etc/shadowsocks.json 
{
"server":"",
"server_port":15959,
"local_address":"127.0.0.1",
"local_port":1080,
"password":"",
"method":"aes-256-cfb",
"fast_open":"true",
"workers":1
}

```

## 浏览器

> 安装SwitchyOmega