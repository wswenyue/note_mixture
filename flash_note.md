#速记

### javah 生成对应类的头文件
```shell
$ javah -classpath $ANDROID_PLATFORMS/android-22/android.jar:. com.xx.Xxx
# -classpath $ANDROID_PLATFORMS/android-22/android.jar 这个如果用到了Android相关的类，必须要添加，比如：Context、Bitmap...
# ":." 如果写了classpath这个一定不能少。表示当前目录也加入到编译目录当中
# 执行命令的目录应该是com.xx.Xxx.class 这个“com”包的父目录下
```
