# Debian 安装 NodeJS

## 方法一 (手动安装)

```
# 下载安装文件
wget https://nodejs.org/dist/v18.15.0/node-v18.15.0-linux-x64.tar.xz

# 解压 tar.xz 到 tar
xz -d node-v18.15.0-linux-x64.tar.xz

# 解压 tar
tar xvf node-v18.15.0-linux-x64.tar

# 重命名文件夹
mv node-v18.15.0-linux-x64/ node-v18
```

配置开发环境 1.修改/etc/profile

```
vim /etc/profile

# 尾部添加以下内容（替换为实际路径）
export PATH=/root/node-v18/bin/:$PATH

# 使环境变量生效
source /etc/profile

```

## 方法二 (自动安装)

使用 NodeSource 安装，具体信息查看：<https://github.com/nodesource/distributions>

```
curl -fsSL https://deb.nodesource.com/setup_lts.x -o nodesource_setup.sh
bash nodesource_setup.sh
apt install -y nodejs
```

检查配置是否成功

```
node -v
npm -v
```
