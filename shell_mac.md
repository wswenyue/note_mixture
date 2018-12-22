# screencapture 截图命令使用
```sh
# 交互方式截图。执行该命令后需要手动框选截图区域
$ screencapture -i test.png
# 截取主显示器
$ screencapture -m test.png

Using:

-c         强制截图保存到剪贴板而不是文件中
-C         截图时保留光标（只在非交互模式下有效）
-d         display errors to the user graphically（不知道啥意思）
-i         交互模式截取屏幕。可以是选区或者是窗口。
             control key - 截图保存到剪贴板
             space key   - 在鼠标选区模式和窗口模式间切换
             escape key  - 退出截图
-m         只截取主显示器（-i模式下无效）
-M         截图完毕后，会打开邮件客户端，图片就躺在邮件正文中
-o         在窗口模式下，不截取窗口的阴影
-P         截图完毕后，在图片预览中打开
-s         只允许鼠标选择模式
-S         窗口模式下，截取屏幕而不是窗口
-t<format> 指定图片格式，模式是png。可选的有pdf, jpg, tiff等
-T<seconds> 延时截取，默认为5秒。
-w         只允许窗口截取模式
-W         开始交互截取模式，默认为窗口模式（只是默认模式与-i不同）
-x         不播放声效
-a         do not include windows attached to selected windows（不懂）
-r         不向图片中加入dpi信息
-l<windowid> 抓取指定windowid的窗口截图
-R<x,y,w,h> 抓取指定区域的截图
-B<bundleid> 截图输出会被bundleid指出的程序打开
```