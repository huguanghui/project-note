[TOC]

# Curl的编译

## 下载

- [curl](https://curl.haxx.se/download.html)      -支持文件的上传和下载.支持HTTP,HTTPS和FTP等各种协议.
- [zlib](http://www.zlib.net/)       -数据压缩功能 
- [openssl](https://oomake.com/download/openssl)   -安全套接字层密码库，囊括主要的密码算法、常用的密钥和证书封装管理功能及SSL协议
- [libssh2](https://www.libssh2.org/)     -SSH2是一套安全通讯协议框架
- [curl使用样例](https://curl.haxx.se/libcurl/c/example.html)

## curl的API使用

### 1. FTP的下载和上传

- 准备一个Ftp的服务器

### 2. 下载 github 中某个仓库中的文件

```shell
$ curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/uninstall.sh
$ curl -fsSL https://github.com/LeCoupa/awesome-cheatsheets/raw/master/languages/C.txt
```

### 3. 使用命令调用 HTTP 方法

```shell
# GET 方法
$ curl http://localhost:8000/api/v1/a
# POST 方法
$ curl -d "user=admin&passwd=12345678" http://127.0.0.1:8080/login
```

