### 查看进程

命令：

```sh
adb shell ps
```

输出示例：

```sh
USER     PID   PPID  VSIZE  RSS     WCHAN    PC        NAME
root      1     0     8904   788   ffffffff 00000000 S /init
root      2     0     0      0     ffffffff 00000000 S kthreadd
...
u0_a71    7779  5926  1538748 48896 ffffffff 00000000 S com.sohu.inputmethod.sogou:classic
u0_a58    7963  5926  1561916 59568 ffffffff 00000000 S org.mazhuang.boottimemeasure
...
shell     8750  217   10640  740   00000000 b6f28340 R ps
```

各列含义：

| 列名   | 含义     |
| ---- | ------ |
| USER | 所属用户   |
| PID  | 进程 ID  |
| PPID | 父进程 ID |
| NAME | 进程名    |

### 查看实时资源占用情况

命令：

```sh
adb shell top
```

输出示例：

```sh
User 0%, System 6%, IOW 0%, IRQ 0%
User 3 + Nice 0 + Sys 21 + Idle 280 + IOW 0 + IRQ 0 + SIRQ 3 = 307

  PID PR CPU% S  #THR     VSS     RSS PCY UID      Name
 8763  0   3% R     1  10640K   1064K  fg shell    top
  131  0   3% S     1      0K      0K  fg root     dhd_dpc
 6144  0   0% S   115 1682004K 115916K  fg system   system_server
  132  0   0% S     1      0K      0K  fg root     dhd_rxf
 1731  0   0% S     6  20288K    788K  fg root     /system/bin/mpdecision
  217  0   0% S     6  18008K    356K  fg shell    /sbin/adbd
 ...
 7779  2   0% S    19 1538748K  48896K  bg u0_a71   com.sohu.inputmethod.sogou:classic
 7963  0   0% S    18 1561916K  59568K  fg u0_a58   org.mazhuang.boottimemeasure
 ...
```

各列含义：

| 列名   | 含义                                     |
| ---- | -------------------------------------- |
| PID  | 进程 ID                                  |
| PR   | 优先级                                    |
| CPU% | 当前瞬间占用 CPU 百分比                         |
| S    | 进程状态（R=运行，S=睡眠，T=跟踪/停止，Z=僵尸进程）         |
| #THR | 线程数                                    |
| VSS  | Virtual Set Size 虚拟耗用内存（包含共享库占用的内存）    |
| RSS  | Resident Set Size 实际使用物理内存（包含共享库占用的内存） |
| PCY  | 调度策略优先级，SP_BACKGROUND/SPFOREGROUND     |
| UID  | 进程所有者的用户 ID                            |
| NAME | 进程名                                    |

`top` 命令还支持一些命令行参数，详细用法如下：

```sh
Usage: top [ -m max_procs ] [ -n iterations ] [ -d delay ] [ -s sort_column ] [ -t ] [ -h ]
    -m num  最多显示多少个进程
    -n num  刷新多少次后退出
    -d num  刷新时间间隔（单位秒，默认值 5）
    -s col  按某列排序（可用 col 值：cpu, vss, rss, thr）
    -t      显示线程信息
    -h      显示帮助文档
```

```sh
eg:查看com.tencent相关的进程线程的实时cpu占用
$ top -n 3 -s cpu -t |grep "com.tencent"
```