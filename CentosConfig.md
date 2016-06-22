# Centos

`rpm -ivh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm`

## 新建centos虚拟机初始化配置
1. 生成`sshkey` 命令 `ssh-keygen`
2. 保存本地`sshkey` 进行ssh无密登陆 `authorized_keys`
3. 更新yum更新   `yum -y update`
4. 修改服务器名 `hostnamectl set-hostname whis `
5. `uname -a` 查看服务器系统
6. `systemctl stop firewalld.service` 关闭防火墙,根据实际需求来

> `-bash: ifconfig: command not found`遇到该问题，`yum install net-tools` 后执行 `ifconfig`

##Oh-my-zsh install
>参考文档：
>[终极 Shell——ZSH](https://zhuanlan.zhihu.com/p/19556676)      
>[oh-my-zsh github](https://link.zhihu.com/?target=https%3A//github.com/robbyrussell/oh-my-zsh)    
>[autojump](https://github.com/wting/autojump)

- `cat /etc/shells`   查看当前系统中有几种shell
- `chsh -s /bin/zsh`  将当前系统的bash shell 切换成zsh
- `sudo yum install zsh` OR `sudo apt-get install zsh` 如果发现当前系统中没有可进行该命令进行安装，mac下自带
- `yum install vim git`
- 手动安装    
`git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh`
`cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`
- `git clone git@github.com:wqcsimple/mac_config.git` OR `git clone https://github.com/wqcsimple/mac_config.git` 个人的配置文件github地址
- `cd mac_config && cp ./zshrc ../.zshrc && cp ./vimrc ../.vimrc`
- `wget https://github.com/downloads/joelthelion/autojump/autojump_v21.1.2.tar.gz` 安装autojump，下载完成后解压`tar zxvf filename` 进入目录`./install.sh`, `[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh`将代码加入到`.zshrc`

```
ssh-rsaAAAAB3NzaC1yc2EAAAADAQABAAABAQDVNGe8y2be5IqwY2uMLoFR7s6BlTw6WUL24WCZu4Z81BLfthLso6BIys2lebSKBXUWlSeRcisUC45Zr4lJek666th/eZ+yKpGv4cQwRffFKedl36gTLa1R7wtHUh1OtdLiauad5d/8RbA6T6wGeJ6LatONTRFE+vhD1VzY0OTNVX03XNQgUOhz9g+wLHbPpdkhv15pdu5Z8Hi3BCDtmJiBPRy7E1izHYxAoJz6tQqroIvQG6CcJ2WTRGNQC6CVyP+gCQGKFUdD1OBC6O3CNZ/IRm8fuqv6PyAyEyWBmwSx0Zof8x/d6txmMRRwHJG1gRgF7PAEWx8ifwW/M8qCZMlF dev@devdeMacBook-Pro.local
```
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVNGe8y2be5IqwY2uMLoFR7s6BlTw6WUL24WCZu4Z81BLfthLso6BIys2lebSKBXUWlSeRcisUC45Zr4lJek666th/eZ+yKpGv4cQwRffFKedl36gTLa1R7wtHUh1OtdLiauad5d/8RbA6T6wGeJ6LatONTRFE+vhD1VzY0OTNVX03XNQgUOhz9g+wLHbPpdkhv15pdu5Z8Hi3BCDtmJiBPRy7E1izHYxAoJz6tQqroIvQG6CcJ2WTRGNQC6CVyP+gCQGKFUdD1OBC6O3CNZ/IRm8fuqv6PyAyEyWBmwSx0Zof8x/d6txmMRRwHJG1gRgF7PAEWx8ifwW/M8qCZMlF dev@devdeMacBook-Pro.local
```

## nginx 
- `yum install epel-release`
- `yum install nginx`

