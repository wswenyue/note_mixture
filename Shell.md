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