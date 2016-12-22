##  Centos 配置备忘

## 设置系统代理
编辑文件 `/etc/profile`
添加以下代码
```
## add proxy for network
export http_proxy="http://aly-sh-1.p.nac.innotick.com:10006"
```
`source /etc/profile` 生效


## 设Shadowsocks代理
- `yum -y install epel-release` 安装扩展源
- `yum -y install python-pip`
- `pip install --upgrade pip` 升级
- `pip install shadowsocks`
- `ssserver --help`  查看帮助
- `sslocal -c /eta/shadowsocks.json` 启动

```
{
    "server" : "100.100.100.100",
    "server_port" : 8888,
    "local_port" : 1080,
    "password" : "123456",
    "timeout" : 600,
    "method" : "aes-256-cfb"
}
```

## 新建启动脚本文件/etc/systemd/system/shadowsocks.service，内容如下：
```
[Unit]
Description=Shadowsocks

[Service]
TimeoutStartSec=0
ExecStart=/usr/bin/ssserver -c /etc/shadowsocks.json

[Install]
WantedBy=multi-user.target

```

## 执行以下命令启动 shadowsocks 服务：
`systemctl enable shadowsocks`
`systemctl start shadowsocks`
`systemctl status shadowsocks -l`

## 更新yum源

1. `cd /etc/yum.repos.d`
2. `mv CentOS-Base.repo CentOS-Base.repo.backup`
3. `wget http://mirrors.163.com/.help/CentOS7-Base-163.repo`
4. `mv CentOS6-Base-163.repo CentOS-Base.repo`
5. `yum clean all`


