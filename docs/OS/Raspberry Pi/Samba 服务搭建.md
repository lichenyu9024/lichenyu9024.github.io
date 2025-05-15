# Samba 服务搭建

以下命令都是在 root 用户下操作

## 安装 samba

```bash
apt install samba samba-common-bin -y
vim /etc/samba/smb.conf

# 检查配置文件
testparm
```

## 配置文件

```bash
[global]
# smb ports = 445 139

[shared]
path = /mnt/udisk
public = no
writeable = yes
create mask = 0777
directory mask = 0777
```

## 启动、停止或重启 samba 服务

```bash
systemctl start smbd
systemctl stop smbd
systemctl restart smbd
```

## 用户配置

```bash
# 新增用户，用户专门用来浏览 smb
adduser shared

# 为这个用户分配smb独立密码
smbpasswd -a shared
```

## 配置 U 盘作为共享文件目录

### 创建目录

```bash
mkdir /mnt/udisk
chmod 777 -R /mnt/udisk
```

### 清空并格式化 U 盘（可选）

查看设备信息与 UUID 信息

```bash
# 查看设备信息
lsblk
# 查看指定设备的UUID
blkid /dev/sda1
# 查看文件系统信息
df -hT
```

清空 U 盘，建议分区为 ext4，Linux 下 exfat、ntfs 可能会出问题

```bash
# 清空U盘并重新分区
fdisk /dev/sda
(使用 d 删除原有分区，使用 n p 添加一个分区)

# 格式化分区
mkfs.ext4 /dev/sda1
```

### 挂载 U 盘

```bash
# 手动挂载U盘
mount /dev/sda1 /mnt/udisk
# 手动卸载U盘
umount /mnt/udisk

# 自动挂载：配置文件系统表
vim /etc/fstab
# 添加内容（修改UUID为你的设备的UUID）
# 挂载设备  挂载点  文件系统类型    文件系统参数    备份命令    是否以fsck检验扇区
UUID=98650d8a-8031-43ee-93b5-53fbca3165c0    /mnt/udisk    ext4    defaults    0    0
```

## Windows 断开 smb 连接

```powershell
net use * /del
net use * /del /y
```
