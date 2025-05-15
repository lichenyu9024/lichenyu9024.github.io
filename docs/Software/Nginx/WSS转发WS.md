# WebSocket WSS - WS

1.为你的域名站点设置好SSL，能够正常https访问

2.打开站点的nginx配置文件

3.server顶部添加以下内容（端口修改为你的wss服务监听的端口）：

```
map $http_upgrade $connection_upgrade {
    default upgrade;
    '' close;
}
upstream websocket {
    server 127.0.0.1:9028;
}
```


4.在 #SSL-END 这串注释的后面添加以下内容（端口修改为你的wss服务监听的端口）：

```
location / {
    proxy_pass http://127.0.0.1:9028;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "Upgrade";
}
```

5.保存

6.访问"wss://域名"即可连接wss服务
