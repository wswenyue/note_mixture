# git 相关

### 查询master分支 push、fetch时间
```sh
$  git reflog origin/master --date=iso 
```

### BFG 使用 - git历史修改者

删除git历史中误提交的某个文件夹
```sh
# 1.删除git历史中误提交的某个文件夹 eg：.gradle/*
# --no-blob-protection :表示不需要保护。bfg默认会保护HEAD版本，设置该字段后就不会在保护，如果不需要修改头指针那是比较好的。
# .git 是当前项目的git
$ java -jar ~/Downloads/bfg-1.13.0.jar --delete-folders .gradle .git --no-blob-protection

# 2. 整理relog 和通知gc处理
$ git reflog expire --expire=now --all && git gc --prune=now --aggressive

# 3. 推送到远程仓库，如果涉及修改了HEAD那么就需要强制覆盖push
$ git push
# 4. 本地如果有问题，那么直接删除本地项目文件，重新拉取即可。
```