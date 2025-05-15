# Debian 桌面版常见问题

## 软件源问题

针对 debian12

```
echo "修改软件源"
echo "deb https://mirrors.ustc.edu.cn/debian/ bookworm main contrib non-free non-free-firmware" > /etc/apt/sources.list
echo "deb-src https://mirrors.ustc.edu.cn/debian/ bookworm main contrib non-free non-free-firmware" >> /etc/apt/sources.list
```

## 用户不在 sudoer 中 （Username is not in the sudoers file）

使用 root 用户登录系统，运行以下命令

```
echo "添加用户到 sudo 组"
usermod -aG sudo username
```
