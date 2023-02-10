# FFmpeg

## 学习指南

马如林项目使用

* 推拉流
* 合成流
* 图片转视频
* 合成音频到视频
* 合成字幕到视频
* 视频流添加字幕

### 常用命令

#### 简单的举几个例子

* ffmpeg -i input.mp4 output.avi
  * 转换输入mp4到avi
* ffmpeg -y -f concat -safe 0 -i merge.txt -c copy -shortest output.mp4
  * 合并多个文件

    ``` shell
    $ cat merge.txt
    file '/Users/rollin/Desktop/AIWord1.0/500/av/aiffJpg/1-the_1.mp4'
    file '/Users/rollin/Desktop/AIWord1.0/500/av/aiffJpg/2-be_1.mp4'
    file '/Users/rollin/Desktop/AIWord1.0/500/av/aiffJpg/3-and_1.mp4'
    ```

* ffmpeg -i /Users/rollin/word/git/prod/av/aiffJpg/1-the.mp4 -vf ass=/Users/rollin/word/git/prod/subtitle/1-the/1-the-subtitle_1.ass  -y /Users/rollin/word/git/prod/av/aiffJpg/1-the_1.mp4
  * sbutitle.srt 转ass
  * 修改ass的字体设置
  * ffmpeg -i 90-day.mp4 -vf ass=90-day-subtitle.ass f.mp4 执行转换

* ffmpeg -i test.mp4 -filter_complex "drawtext=fontcolor=black:fontsize=40:fontfile=msyh.ttf:text='Summer Video':enable='between(t,1,10)':x=0:y=100" -max_muxing_queue_size 9999  -y output.mp4
  * 添加文字

## 项目实战

* [AI记单词：10000词汇词频顺序基础版（5小时背诵8861个单词）](https://www.bilibili.com/video/BV12b4y1o77R)
  * 这个是我综合使用音视频等技术智能生成的效果，可以搜索AI记单词查找类似视频

## 参考文献

1. [ffmpeg](https://ffmpeg.org)
