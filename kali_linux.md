# Kali Linux 

### 查看系统版本等信息
```sh
$ uname -a
> Linux kali 4.15.0-kali2-amd64 #1 SMP Debian 4.15.11-1kali1 (2018-03-21) x86_64 GNU/Linux
```

### 关机
```sh
# 立即关机
$ shutdown now
```

### 重启
```sh
$ reboot
```

### 设置开机仅启动命令行窗口，不启动GUI界面
```sh
# 设置开启多用户，这样GUI界面就不会打开了
$ systemctl set-default multi-user.target
# 回复到GUI界面可以使用如下指令
$ systemctl set-default graphical.target
```

### SSH Login
```sh
# -p: 指定2200端口而非22端口
# 宿主机连接虚拟机就要使用127.0.0.1的ip,还要给虚拟机设置端口转发，例如：2200转22 
# -i: 指定要用的私钥文件，我们这里使用的是秘钥登录
# -v: 详细输出，一般用于找出ssh连接出错的原因
$ ssh -p 2200 root@127.0.0.1 -i .ssh/id_rsa
```

### SCP 使用ssh通道拷贝文件
```sh
# -P： 指定特别的端口是2200 而非默认端口22
$ scp -P 2200  .ssh/id_rsa.pub root@127.0.0.1:/root/.ssh/host.pub
```