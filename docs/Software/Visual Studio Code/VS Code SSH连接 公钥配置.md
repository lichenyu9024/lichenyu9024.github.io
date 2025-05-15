# VS Code SSH连接 公钥配置

## 密钥生成

密钥的生成可以通过Windows 10生成，也可以通过服务器生成，只要遵循简介中的架构模式即可，这里介绍通过Windows 10生成方式。

1.进入用户文件夹中的".ssh"文件夹

```
比如："C:\Users\xxx\.ssh\"
```

2.运行以下命令建立密钥对

```
ssh-keygen
```

确定保存路径，默认当前目录

输入密码，默认为空(空密码的情况下，连接SSH时就不需要输入密码)

3.上传"id_rsa.pub"文件到服务器用户主目录下的".ssh"文件夹中

```
比如："/home/xxx/.ssh/"或"/root/.ssh/"
```

4.安装公钥

进入用户主目录下的".ssh"文件夹中

运行以下命令

```
cat id_rsa.pub >> authorized_keys
```

之后使用"ls"命令查看一下目录，确保生成"authorized_keys"成功

5.查看或配置打开密钥登录功能

打开服务器SSH配置文件"/etc/ssh/sshd_config"

查看确认以下配置

```
PubkeyAuthentication yes
```

当你完成全部设置，重启SSH

```
service sshd restart
```

