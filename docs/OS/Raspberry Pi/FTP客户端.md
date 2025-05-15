# 安装FTP客户端

1.安装vsftpd服务器

```
sudo apt-get install vsftpd
```

2.启动ftp服务

```
sudo service vsftpd start
```

3.编辑vsftdp配置文件

```
sudo nano /etc/vsftpd.conf

不允许匿名访问
anonymous_enable=NO

设定本地用户可以访问
local_enable=YES   
 
设定可以进行写操作
write_enable=YES

设定上传后文件的权限掩码
local_umask=022
```

4.按 ctrl-o 保存，按 ctrl-x 关闭
5.重启ftp服务

```
sudo service vsftpd restart
```
6.至此，FTP服务就安装配置好了
7.windows登录FTP：资源管理器中输入:"ftp://192.168.1.x"
