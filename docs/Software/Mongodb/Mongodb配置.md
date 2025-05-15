## 配置 MongoDB 文件

vim /etc/mongod.conf

```
net:
  bindIp: 0.0.0.0
security:
    authorization: "enabled"
```

## 使用 root 用户修改配置文件可能导致 MongoDB 无法启动

修改 MongoDB 文件权限

```
chown -R mongodb:mongodb /var/lib/mongodb/
chown mongodb:mongodb /tmp/mongodb-27017.sock
```
