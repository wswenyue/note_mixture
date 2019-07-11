# shell 篇

### 字符串tr处理使用

|  规则   |                    示例                    |
| :---: | :--------------------------------------: |
| 大写转小写 | `tr '[:upper:]' '[:lower:]'` OR `tr '[A-Z]' '[a-z]'` |
| 删除字符  |           `tr -d x`  x:要删除的字符            |
| 字符替换  |             `tr A B`  把A替换成B             |

### xargs 使用
> xargs能够处理管道或者stdin并将其转换成特定命令的命令参数
>
```bash
#复制所有图片文件到 /data/images 目录下
$ ls *.jpg | xargs -n1 -I cp {} /data/images
# 删除当前目录下所有的log文件
# xargs 默认是以空白字符，如果文件名中包含空白符号会出错，find打印文件后面加入'\0',xargs 以 '\0'分割就可以解决这个问题
$ find . -type f -name "*.log" -print0 | xargs -0 rm -f
# 统计一个源代码目录中所有php文件的行数
$ find . -type f -name "*.php" -print0 | xargs -0 wc -l
# 查找所有的jpg 文件，并且压缩它们
$ find . -type f -name "*.jpg" -print | xargs tar -czvf images.tar.gz
# -dX :以'X'分割; -n2 :一行（一批）输出两个
$ echo "nameXnameXnameXname" | xargs -dX -n2
-> name name
-> name name
```

### 去重 `uniq` `sort -u`
> `uniq`  只能识别临近的相同行
> `sort -u` 是全文本去重

### `cut` 字符串切割
```bash
# 以‘X’切割并取第二组字符串
$ echo "abXbcXdeX" |cut -d "X" -f 2
--> bc
```
### `tee` 指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件
```bash
$ echo "hello" |tee backup.txt
```

### js 文件压缩、混淆
```sh
$ npm install uglify-js -g 
# 全局安装uglify-js
$ uglifyjs input.js -c -m -o out-min.js
# input.js :要压缩的js文件
# out-min.js :压缩后的文件路径
# -c :压缩 ; -m :单字母混淆; -o :输出

$ uglifyjs out-min.js -b -o abc.js
# -b :格式化js
```

### 在流输出情况下，grep,tee等指令的串联使用
```sh
# --line-buffered:流输出的情况下，必须指定buffer大小为行大小
# -E :是正则支持
# 后面追加 |grep -E "Networks|Disks"是想要输出在终端的内容，有高亮显示
$ top |grep --line-buffered -E "Networks|Disks" |tee Desktop/log.txt |grep --line-buffered -E "Networks|Disks"
```

### grep
```sh
# 遍历搜索当前文件夹下面所有文件中包含text的行 -r：遍历所有子文件夹
$ grep -r text ./
```

### diff 指令使用
```sh
# 以并列的方式显示文件的异同之处
$ diff -y dir1 dir2
# 以并列的方式显示两个内容的异同之处；右边部分只显示不一样的
$ diff -y --left-column  <(ls dir1) <(ls dir2)
# 以并列的方式显示两个内容的异同之处；只显示不一样的部分
$ diff -y --suppress-common-lines <(ls dir1) <(ls dir2)
# 对比两个文件内容
$ icdiff projects/{app1,app2}/settings.gradle
```
### 格式转换
```sh
# 将pdf转成png格式
$ sips -s format png a.pdf --out img.png
```