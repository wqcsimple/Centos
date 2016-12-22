## 设置代理  安装
```shell
yum install -y gcc
yum install -y gcc-c++ make

mkdir -p /opt/package
cd /opt/package
git clone https://github.com/rofl0r/proxychains-ng.git proxychains-ng
cd proxychains-ng
./configure --prefix=/usr --sysconfdir=/etc
make && make install && make install-config
```

##  替换配置文件
`/etc/proxychains.conf`

## 使用前加 `proxychains4`
