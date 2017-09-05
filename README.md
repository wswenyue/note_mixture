# 杂记

### [懒加载Fragment 让应用更优化](http://immortalz.me/262.html)
> 懒加载，可以处理相机权限初始化等相关的问题，还可以优化网络请求，优化内存

### Android 秘钥生成

```bash
$ keytool -genkey -alias ifdebugkey -keyalg RSA -validity 20000 -keystore ifdebug.keystore
```
> ifdebugkey : alias name   
> ifdebug.keystore : key file name

### 查看秘钥内容

- 查看秘钥文件详细信息

```bash
$ keytool -list -v -keystore ./ifdebug.keystore -storepass xxx
```

- 获取秘钥的MD5信息（小写并且去掉":"）

```bash
$ keytool -list -v -keystore ./ifdebug.keystore -storepass xxx | grep "MD5" | tr '[:upper:]' '[:lower:]' |tr -d :
```

### shell 中 字符串tr处理使用

规则|示例
:--:|:--:
大写转小写|`tr '[:upper:]' '[:lower:]'` OR `tr '[A-Z]' '[a-z]'`
删除字符|`tr -d x`  x:要删除的字符
字符替换|`tr A B`  把A替换成B

