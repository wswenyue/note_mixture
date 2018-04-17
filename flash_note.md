# 速记

###  javah 生成对应类的头文件
```shell
$ javah -classpath $ANDROID_PLATFORMS/android-22/android.jar:. com.xx.Xxx
# -classpath $ANDROID_PLATFORMS/android-22/android.jar 这个如果用到了Android相关的类，必须要添加，比如：Context、Bitmap...
# ":." 如果写了classpath这个一定不能少。表示当前目录也加入到编译目录当中
# 执行命令的目录应该是com.xx.Xxx.class 这个“com”包的父目录下
```

### 修改上次commit 的作者信息

```shell
# 修改上次commit 的作者信息
$ git commit --amend --author="Author Name <email@address.com>"
```

### Git ssh多key设置
```shell
# ~/.ssh/config
Host A.com
IdentityFile ~/.ssh/A
User xxx@A.com

Host *
IdentityFile ~/.ssh/id_rsa
User xxx@B.com%
```

###  ssh-keygen 生成秘钥对
```shell
$ ssh-keygen -t rsa -C "xxx@email.com" -f keyFileName
# -t ras ：指定算法RSA
# -C "xxx@email.com" ：指定邮箱
# -f keyFileName ：指定生成秘钥的文件名称
```

### 向 homebrew 贡献 Formula
```sh
# 1. 创建Formula 
$ brew create http://luarocks.org/releases/luarocks-2.3.0.tar.gz
```
### clone 指定层级深度 ，指定分支到本地
```sh
git clone --depth 1 <remote-addr:repo.git> -b <branch-or-tag>
```