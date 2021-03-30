[TOC]

# Go实现MQTT通信

## 安装依赖

```shell
// 先下载golang.org\x\net,由于限制问题,该从github.com/golang中手动下载
go get github.com/eclipse/paho.mqtt.golang
```

## 交互协议



## 相关软件使用

### mosquitto的源码安装和使用

[源码地址](http://mosquitto.org/files/source/)

## 通信流程

1. client订阅/topic/led01
2. client2发送主题为/topic/led01的信息为"hello"

```shell
// mosquitto发送信息
$mosquitto_pub -t topic -m "hello"
// mosquitto订阅
$mosquitto_sub -v -t topic
```

