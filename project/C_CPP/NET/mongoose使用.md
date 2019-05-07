[TOC]

# 使用Mongoose

## 计划目标

- [x] 搭建一个hg工程
- [x] 设计网络配置相关的API接口
- [ ] 使用端口方式先实现功能
- [ ] 改用unix socket方式
- [ ] 测试性能和改善解决方案

## 准备工作

- Mercurial和Trac环境
- mongoose源码
- 参照onvif协议设计网络参数API文档

## 实现步骤

### 1. Merciual搭建新工程

```shell
$ hg init mogo_net    				# 创建mogo_net工程
$ cd mogo_net
# 将mongoose.h mongoose.c和Makefile等文件移入工程中
$ touch .hgignore					# 创建.hgignore文件将过滤不必要的文件
$ hg add *;hg add .hgignore			# 添加修改
$ hg commit -m "1.创建mogo_net工程;\n2.初始化代码仓库;\n"	# 提交修改
$ hg log        # 查看修改记录
```

### 2.引入Trac功能(使用里程碑功能)

```shell
$ mkdir -p /home/hgh/Trac_project/mogo_net    # 创建mogo_net的Trac空工程
$ tracd --port 5000 .						# 开启Trac的网络服务
# 修改conf/trac.ini配置添加源码地址
```

### 3.设计API接口

> 暂时使用文件接口v2.0风格, v3.0风格有待研究

#### 接口说明

- **URL**

> [/Net/NetworkInterface](#)

- **Method**

> GET

- **请求参数**

| 参数 | 类型 | 说明 |
| :--: | :--: | :--: |
|      |      |      |

- **返回参数**

| 参数 | 类型 | 说明 |
| :--: | :--: | :--: |
|      |      |      |
|      |      |      |
|      |      |      |

样例

```json
{
    "NetworkInterfaces": [
        {
            "token": "eth0",
            "Enabled": true,
            "Info": {
                "Name": "eth0"
                "HwAddress": "",
                "MTU": 255
            },
            "Link": {
                "AdminSettings": {
                    "AutoNegotiation": false,
                    "Speed": 100,
                    "Duplex": "Full"
                },
                "OperSettings": {
                    "AutoNegotiation": false,
                    "Speed": 100,
                    "Duplex": "Full"
                },
                "InterfaceType": 6
            },
            "IPv4": {
            	"Enabled": true,
            	"Config": {
                    "Manual"： [ 
                    	{
                            "Address": "",
                            "PrefixLength": 24
                		}
                    ],
                    "LinkLocal"： {
						"Address": "",
            			"PrefixLength": 24
                    },
                    "FromDHCP"： {
						"Address": "",
            			"PrefixLength": 24
                    },
					"DHCP": false
        		}
        	},
            "IPv6": {
				"Enabled": false,
                "Config": {
                    "AcceptRouterAdvert": false,
                    "DHCP": "Off",
                    "Manual": [
                        {
                        	"Address": "",
                        	"PrefixLength": 24                            
                        }
                    ],
                    "LinkLocal": [
                        {
                            "Address": "",
                            "PrefixLength": 24
                    	}
                    ],
                    "FromDHCP": [
                        {
                            "Address": "",
                            "PrefixLength": 24
                    	}
                    ],
                    "FromRA": [
                        {
                            "Address": "",
                            "PrefixLength": 24
                        }
                    ],
                }
            },
            "Extension": {
				"InterfaceType": 6,
                "Dot3": "",
                "Dot11": {
                    "SSID": "",
                    "Mode": "",
                    "Alias": "",
                    "Priority": "",
                    "Security": {
                        "Mode": "WEP",
                        "Algorithm": "CCMP",
                        "PSK": {
                            "Key": "",
                            "Passphrase": "",
                        },
                        "Dot1X": "",
                    }
                }
            }
        }
    ]
}
```

- **URL**

> [/Net/NetworkInterface](#)

- **Method**

> PUT

- **请求参数**

| 参数 | 类型 | 说明 |
| :--: | :--: | :--: |
|      |      |      |

- **返回参数**

| 参数 | 类型 | 说明 |
| :--: | :--: | :--: |
|      |      |      |
|      |      |      |
|      |      |      |

样例
```json
{
    "InterfaceToken": "",
    "NetworkInterface": {
        "Enabled": true,
        "Link": {
            "AutoNegotiation": false,
            "Speed": 100,
            "Duplex": "Full"
        },
        "MTU": 255,
        "IPv4": {
            "Enabled": false,
            "Manual": [
                {
                    "Address": "",
                    "PrefixLength": 24
                }
            ],
            "DHCP": false
        },
        "IPv6": {
            "Enabled": false,
            "AcceptRouterAdvert": false,
            "Manual": [
                {
                    "Address": "",
                    "PrefixLength": ""
                }
            ],
            "DHCP": "Off"
        },
        "Extension": {
            "Dot3": "",
            "Dot11": {
                "SSID": "",
                "Mode": "Ad-hoc",
                "Alias": "",
                "Priority": "",
                "Security": {
                    "Mode": "",
                    "Algorithm": "CCMP",
                    "PSK": {
                        "Key": "",
                        "Passphrase": ""
                    },
                    "Dot1X": ""
                }
            }
        }
    }
}
```

