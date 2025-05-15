Node.js版本列表：
https://nodejs.org/zh-cn/download/releases/

检查树莓派cpu核心：
uname -a

树莓派Zero是"armv6l"
最后支持armv6l的Node版本是v11

下载xxx.tar.xz
wget node.tar.xz

解压
tar -xvf node.tar.xz

解压后，将二进制包移动到/usr/local/node下
sudo mv 你解压的node路径 /usr/local/node

为node和npm建立软连接
sudo ln -s /usr/local/node/bin/node /usr/bin/node
sudo ln -s /usr/local/node/bin/npm /usr/bin/npm

查看node和npm版本的方式来查看是否成功
node -v && npm -v
