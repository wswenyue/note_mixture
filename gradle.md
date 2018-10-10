# gradle 相关


## gradle 常用命令行

using doc  see:
https://docs.gradle.org/current/userguide/command_line_interface.html#example_excluding_tasks

```sh
# 查看项目依赖
$ gradle -q bangjob:dependencies |tee ~/Desktop/dep.txt

# 列出task
$ gradle -q tasks
# 列出所有task
$ gradle -q tasks --all
# 假执行build Task，他的所有Task执行都会被跳过。即可以使用该命令列出build执行的所有task。 
$ gradle build --dry-run

# 执行 dist task 排除test task
$ gradle dist --exclude-task test

# 不管 up-to-date checks，强制执行所有task
$ gradle test --rerun-tasks

# 列出所有的项目，子项目
$ gradle projects

# 查看build Task的帮助，可以输出该Task的详细信息
$ gradle -q help --task build

# 打印对应项目所有的属性值
$ gradle -q bangjob:properties

# 执行clean assembleDebug Task 并设置代理
$ gradle clean assembleDebug -Dhttp.proxyHost=127.0.0.1 -Dhttp.proxyPort=1087 -Dhttps.proxyHost=127.0.0.1 -Dhttps.proxyPort=1087 --info

```