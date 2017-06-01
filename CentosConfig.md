
# [Mac_config][1]

# Centos

`rpm -ivh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-9.noarch.rpm`

`yum update -y`

# apache
`yum -y install httpd mariadb-server php php-devel php-gd php-mbstring php-mcrypt php-pdo php-mysql php-fpm git php-bcmath`

#nginx
`yum -y install nginx mariadb-server php php-devel php-gd php-mbstring php-mcrypt php-pdo php-mysql php-fpm git php-bcmath`


## 新建centos虚拟机初始化配置
1. 生成`sshkey` 命令 `ssh-keygen`
2. 保存本地`sshkey` 进行ssh无密登陆 `authorized_keys`
3. 更新yum更新   `yum -y update`
4. 修改服务器名 `hostnamectl set-hostname whis `
5. `uname -a` 查看服务器系统
6. `systemctl stop firewalld.service` 关闭防火墙,根据实际需求来
7. `vi /etc/resolv.conf` 修改DNS 加上`4.4.4.4`

> `-bash: ifconfig: command not found`遇到该问题，`yum install net-tools` 后执行 `ifconfig`

## 安装rsync
`yum -y install rsync`

##Oh-my-zsh install
>参考文档：
>[终极 Shell——ZSH](https://zhuanlan.zhihu.com/p/19556676)
>[oh-my-zsh github](https://link.zhihu.com/?target=https%3A//github.com/robbyrussell/oh-my-zsh)
>[autojump](https://github.com/wting/autojump)

- `cat /etc/shells`   查看当前系统中有几种shell
- `chsh -s /bin/zsh`  将当前系统的bash shell 切换成zsh
- `sudo yum -y install zsh` OR `sudo apt-get install zsh` 如果发现当前系统中没有可进行该命令进行安装，mac下自带
- `yum install vim git`
- 手动安装
`git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh && cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`
- `git clone git@github.com:wqcsimple/mac_config.git` OR `git clone https://github.com/wqcsimple/mac_config.git` 个人的配置文件github地址
- `cp ./mac_config/zshrc .zshrc && cp ./mac_config/vimrc .vimrc`
- `wget https://github.com/downloads/joelthelion/autojump/autojump_v21.1.2.tar.gz` 安装autojump，下载完成后解压`tar zxvf filename` 进入目录`./install.sh`, `[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh`将代码加入到`.zshrc`


## Centos7 虚拟机配置
### 安装编译工具包
`yum groupinstall -y "Development Tools"`
### 列出服务
`systemctl list-units --type=service`
### 设置时区
`timedatectl set-timezone Asia/Shanghai`
### 关闭IPV6
`sysctl -w net.ipv6.conf.all.disable_ipv6=1`
`sysctl -w net.ipv6.conf.default.disable_ipv6=1`
### 设置生效
`sysctl -p`
### 清空yum临时文件
`yum clean all`

## nginx
- `yum install epel-release`
- `yum install nginx`

[1]: https://github.com/wqcsimple/mac_config



##  修改时区

`yum install tzdata -y`

`cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`

`echo "Asia/Shanghai" > /etc/timezone`

`date`