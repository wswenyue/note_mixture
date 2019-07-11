# 格式转换
```sh
# webm(视频) 转换成MP3(品质为320K)
# -ab : audio bit rate
# -ar : audio sample rate
# -i : 输入
# -y : 输出
# -vn : 过滤video
$ ffmpeg -i in.webm -vn -ab 320K -y out.mp3
# 过滤调视频轨。输出的音频编码使用源视频的音频编码
$ ffmpeg -i in.webm -vn -acodec copy -y out.webm
```


# useful links

https://gist.github.com/protrolium/e0dbd4bb0f1a396fcb55