# Manjaro 安装 KVM 虚拟机

## 检查处理器是否支持虚拟化

```
LC_ALL=C lscpu | grep Virtualization
```

AMD 处理器显示：

```
Virtualization: AMD-V
```

## 安装 KVM

```
pacman -S qemu libvirt virt-manager virt-viewer
pacman -S ovmf dnsmasq vde2 bridge-utils openbsd-netcat ebtables iptables
```

- qemu 向 Guest OS 模拟硬件（例如，CPU，网卡，磁盘，等）
- libvirt 提供管理虚拟机和其它虚拟化功能的工具和 API
- virt-manager 是管理虚拟机的 GUI
- virt-viewer 虚拟机图形界面展示工具
- ovmf 为虚拟机启用 UEFI 支持
- dnsmasq 配置 DNS 和 DHCP 的工具
- bridge-utils 配置网桥
- openbsd-netcat 大名鼎鼎的 netcat
- ebtables 内部防火墙，管理虚拟机的通信
- iptables 外部防火墙，一般 Linux 都有

## 启动服务

```
# sudo
systemctl enable libvirtd.service
systemctl startlibvirtd.service
systemctl status libvirtd.service
virsh net-start default
virsh net-autostart default
```

## 查看你所在的组是否包含 libvirt

id username

## 不包含的情况，则添加你的用户到 libvirt 组中

usermod -aG libvirt username

## 打开虚拟机

找到菜单里的 Virtual Machine Manager，虚拟机管理，打开即可

或者运行 virt-manager
