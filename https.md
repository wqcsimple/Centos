
certbot certonly --standalone -m sinfere@gmail.com \
  -d di.sinfere.com \
  -d api.lishu.sinfere.com \
  -d api.upark.innotick.com \
  -d api.tms.sinfere.com \
  -d api.mall.pinjia.sinfere.com \
  -d api.rent.pinjia.sinfere.com \
  -d api.ynr.sinfere.com


  certbot certonly --standalone -m wqcsimple@foxmail.com \
    -d whis.wang \
    -d www.whis.wang

## 自己的服务器
certbot certonly --standalone -m wqcsimple@foxmail.com \
    -d wwhis.com \
    -d whis.wang \
    -d test.wwhis.com


[参考链接](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwiBnaOxn63TAhVDv7wKHa2qCzEQFgglMAA&url=https%3A%2F%2Fcertbot.eff.org%2F&usg=AFQjCNGy31LL0l1YWybeVw8XwA_7DCrUZw&sig2=gkUbuXEMNrT0E9MYvkD8MQ)


# sinfere 服务器
```shell
certbot certonly --standalone -m sinfere@gmail.com \
  -d di.sinfere.com \
  -d blua-api.sinfere.com \
  -d api.lishu.sinfere.com \
  -d api.upark.innotick.com

cat cert.pem chain.pem privkey.pem > prod.pem
/usr/bin/cp prod.pem /etc/haproxy/prod.pem
```



## 安装certbot
```shell
wget https://mirrors.aliyun.com/centos/7.6.1810/cloud/x86_64/openstack-ocata/python2-pyOpenSSL-16.2.0-3.el7.noarch.rpm
sudo rpm -Uvh python2-pyOpenSSL-16.2.0-3.el7.noarch.rpm
sudo yum install certbot -y
sudo certbot certonly

安装好的目录
/etc/letsencrypt/live/wwhis.com
生成密钥
cat cert.pem chain.pem privkey.pem > prod.pem
/usr/bin/cp prod.pem /etc/haproxy/prod.pem
```

##  关于安装不成功的解决方案
```shell
pip uninstall urllib3
pip install --upgrade urllib3
yum erase pyOpenSSL

pip uninstall urllib3
pip uninstall requests
pip uninstall chardet
yum remove python-requests
yum remove python-urllib3
pip install --upgrade --force-reinstall 'requests==2.6.0' urllib3
yum install certbot
```
> https://www.centos.bz/2017/09/centos7-certbot-python-urllib3/
> https://www.yuzhi100.com/article/centos-7-certbot-pyopenssl-missing-required-functionality