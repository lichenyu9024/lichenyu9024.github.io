# websocketd

官方网：http://websocketd.com/
GitHub：https://github.com/joewalnes/websocketd/releases

### 下载websocketd，解压websocketd.zip，把websocketd添加到系统环境变量

#### CentOS:
修改 ~/.bash_profile 文件，把如下代码(替换你实际的路径)，加入到 "PATH=$PATH:$HOME/bin" 该行之后（注意以冒号分隔）,保存文件并退出。
```
:/www/wwwroot
```
执行 source ~/.bash_profile 使其生效

### 运行 websocketd

确保防火墙与安全组开放了自定义的端口，这里设端口为3006

```
websocketd --port=3006 -devconsole  php /www/Server.php
```

在http中链接服务器：http://xxx.com:3006	(ws://xxx.com:3006)

### 运行 websocketd SSL方式

```
websocketd --port=3006 --sslcert="/xxx.pem" --sslkey="/xxx.pem" php /www/Server.php
```

在https中链接服务器：https://xxx.com:3006	(wss://xxx.com:3006)

### 运行 websocketd（开发者控制台）

```
websocketd --port=3006 -devconsole  php /www/Server.php
```

### 后台运行 websocketd

```
nohup websocketd --port=3006 php /www/Server.php &
```

"&"号不能少

### 杀死后台运行的websocketd进程：
查找websocketd的PID，干掉websocketd

```
ps -ef|grep websocketd
kill PID
```

### 配置Nginx反向代理：wss（可选）

1、网站需要先配置好SLL（HTTPS）
2、配置nginx站点（站点配置，不是nginx总配置）

```
# wss协议转发,访问：wss://xxxx.com/wss
location /wss
{
  proxy_pass http://127.0.0.1:3006;
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "Upgrade";
  proxy_set_header X-Real-IP $remote_addr;
}
```

在https中链接服务器：https://xxx.com/wss	(wss://xxx.com/wss)

## 一些记录

使用socket传输信息的时候，整个信息为一串字符
换行符（\n）只能有一个，一个换行为一条信息
使用php传信息的时候一般需要手动添加换行符

STDIN：从客户端接收的信息
STDOUT：发给客户端的信息