# Debian 添加 Swap 分区

## 准备工作

1.检查是否存在 Swap 分区

```
swapon -s
free -m
```

如果没有返回结果或者 free -m 中 Swap 一列数值是 0，则表示你的系统没有 Swap 分区。

2.检查当前磁盘剩余空间

```
df -h
```

## 创建 Swap 分区

使用 fallocate 命令创建一个 4GB 大小的 Swap 分区
如果这个命令无法使用，请安装 util-linux 包 (apt install util-linux)

```
fallocate -l 4G /swapfile

# 设置文件权限
chmod 600 /swapfile

# 激活Swap分区
mkswap /swapfile
swapon /swapfile

# 设置开机自动挂载
echo "/swapfile swap swap defaults 0 0" >> /etc/fstab
```

## 大功告成

查看 Swap 分区是否正确

```
swapon -s
free -m
```

## 关闭 Swap

```
# 停用Swap分区
swapoff -v /swapfile

# 检查 /etc/fstab，删除下面这一行
/swapfile swap swap defaults 0 0

# 删除 /swapfile 这个文件
rm /swapfile
```
