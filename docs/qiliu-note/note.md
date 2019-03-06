#  智能日志平台

## 数据上传

### 文件上传

### Logkit Pro收集

[Logkit Pro](https://logkit-pro.qiniu.com/#/)

#### Mac

```shell
export QINIU_ACCESS_KEY=E9lIAfLisSh9xdHl4nhaqWbRIV82J4knAv2ZxmNz;export QINIU_SECRET_KEY=GpgZ8Q9rMyLOA7TejtnQPStxKYUJsSLyI3e8la8N;export QINIU_EMAIL=522146829@qq.com;curl -L 'https://logkit-pro.qiniu.com/v1/install/f9d1f400c956af83cd1e2ddc7e5af54b/sh?tags=' | bash
```

#### Linux

```shell

```

### Docker方式部署

```shell
$docker pull qiniupandora/logkit:v1.2.4
$docker run -d -p 3000:3000 -e QINIU_ACCESS_KEY='E9lIAfLisSh9xdHl4nhaqWbRIV82J4knAv2ZxmNz' -e QINIU_SECRET_KEY='GpgZ8Q9rMyLOA7TejtnQPStxKYUJsSLyI3e8la8N' -v /local/logkit/meta:/app/meta -v /local/logkit/.logkitconfs:/app/.logkitconfs -v /local/logkit/dataconf:/app/confs -v /local/log/path:/logs/path qiniupandora/logkit:v1.2.4
```

