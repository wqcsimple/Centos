## 为了安全而战
> 自己的美国服务器被全世界的人暴力ssh破解,下面记录防护的过程

###  修改SSH配置文件
```
vi /etc/ssh/sshd_config

#禁用密码验证
PasswordAuthentication no
#启用密钥验证
RSAAuthentication yes
PubkeyAuthentication yes
#指定公钥数据库文件
AuthorsizedKeysFile .ssh/authorized_keys

service sshd restart 重启ssh服务
systemctl restart sshd.service
```


### 查看登录历史
```
last
last {用户} 查看指定用户

root     pts/0        117.149.0.120    Sat Apr  1 11:56   still logged in
root     pts/0        117.149.0.120    Sat Apr  1 11:44 - 11:46  (00:01)
root     pts/0        60.186.168.2     Sat Apr  1 00:16 - 01:56  (01:39)
root     pts/0        117.149.0.120    Fri Mar 31 19:30 - 19:31  (00:00)
root     pts/0        117.149.0.120    Fri Mar 31 18:20 - 19:14  (00:54)
root     pts/0        117.149.0.120    Thu Mar 30 19:05 - 19:06  (00:01)
root     tty1                          Mon Mar 20 13:15   still logged in
reboot   system boot  3.10.0-514.6.2.e Mon Mar 20 21:14 - 12:14 (11+15:00)

wtmp begins Fri Feb 24 03:09:44 2017
```

### 查看当前登录用户
```
who

root     tty1         2017-03-20 13:15
root     pts/0        2017-04-01 11:56 (117.149.0.120)
第一列是用户名,
第二列是连接的终端,tty表示显示器,pts表示远程连接,
第三列是登陆时间,

查看当前用户行为
> # w
> # w {用户} 查看指定的用户
 12:19:26 up 11 days, 23:05,  2 users,  load average: 0.00, 0.01, 0.05
}
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     tty1                      20Mar17 11days  0.00s  0.00s -bash
root     pts/0    117.149.0.120    11:56    6.00s  0.39s  0.00s w
```


