# 安装python版的shadowsocks

## 安装shadowsocks
`curl --show-error --retry 5 https://bootstrap.pypa.io/get-pip.py | python`
`pip install shadowsocks`

这时系统会多出两个命令
```
/usr/bin/ssserver
/usr/bin/sslocal

# 运行帮助命令
ssserver -h
usage: ssserver [OPTION]...
A fast tunnel proxy that helps you bypass firewalls.

You can supply configurations via either config file or command line arguments.

Proxy options:
  -c CONFIG              path to config file
  -s SERVER_ADDR         server address, default: 0.0.0.0
  -p SERVER_PORT         server port, default: 8388
  -k PASSWORD            password
  -m METHOD              encryption method, default: aes-256-cfb
  -t TIMEOUT             timeout in seconds, default: 300
  --fast-open            use TCP_FASTOPEN, requires Linux 3.7+
  --workers WORKERS      number of workers, available on Unix/Linux
  --forbidden-ip IPLIST  comma seperated IP list forbidden to connect
  --manager-address ADDR optional server manager UDP address, see wiki

General options:
  -h, --help             show this help message and exit
  -d start/stop/restart  daemon mode
  --pid-file PID_FILE    pid file for daemon mode
  --log-file LOG_FILE    log file for daemon mode
  --user USER            username to run as
  -v, -vv                verbose mode
  -q, -qq                quiet mode, only show warnings/errors
  --version              show version information

Online help: <https://github.com/shadowsocks/shadowsocks>
```

## 编写开机启动脚本

### 方法一: 编写shadowsocks.json文件
```
vi /opt/shadowsocks/shadowsocks.json
单用户
{
    "server":"",
    "server_port": 10001,
#    "local_address": "127.0.0.1",
#    "local_port":1080,
    "password":"",
    "timeout":60,
    "method":"aes-256-cfb"
}
多用户版
{
    "server":"",
#    "server_port": 10001,
#    "local_address": "127.0.0.1",
#    "local_port":1080,
     "port_password": {
         "10001": "whis.wang1992",
         "10002": "wwhis.com"
     },
#    "password":"",
    "timeout":60,
    "method":"aes-256-cfb"
}


ssserver -c /opt/shadowsocks/shadowsocks.json -d start 启动
ssserver -c /opt/shadowsocks/shadowsocks.json -d stop  停止

less /var/log/shadowsocks.log
```
### 方法二：编写开机启动脚本
执行`vim /etc/rc.d/rc.local`，添加以下内容。最后别忘了执行`chmod +x /etc/rc.d/rc.local`以赋予其执行权限！
# 用户一
`ssserver -c /opt/shadowsocks/shadowsocks.json --pid-file /tmp/ss1.pid -d start`

# 直接跑
`ssserver -p 10001 -k whis.wang992 -m rc4-md5 --workers 10 --pid-file /tmp/ss.pid --log-file /opt/shadowsocks/ss.log --user nobody -v -d start`

# 各参数作用
```
-p ss服务器的端口号
-k 密码
-m 加密方式，一般用rc4-md5，table和rc4不要用
--workers 子进程个数
--pid-file 记录pid的文件
--log-file 记录日志
--user 执行用户的权限，一般使用nobody
-v 表示输出详细信息
-d 使用守护进程模式运行
```




`./ss-local -s 127.0.0.1 -p 5292 -k AYpX4GwX99 -m aes-128-cfb -l 5291 -b 0.0.0.0`

curl -v -x socks5://127.0.0.1:6255 'http://www.baidu.com'





服务器 149.202.159.183
端口 10002
密码 whis.wang
加密方式 aes-256-cfb