Atitit 直播推拉流测试

vlc播放器拉流
在vlc播放器媒体菜单里打开网络串流，网络URL填写 rtmp://127.0.0.1:1935/myapp/test 点击播放

ffmpeg进行推流

ffmpeg -re -i video.mp4 -f flv rtmp://127.0.0.1:1935/myapp/test


D:\ffmpegbin\ffmpeg.exe -re -i d:/ccc/a.mp4 -f flv rtmp://155484.livepush.myqcloud.com/live_appnm1/strm_nm?txSecret=13e0506e53634532d2c2686867d39e4b&txTime=61CE8FBE

D:\ffmpegbin\ffmpeg.exe -re -i d:/ccc/a.mp4 -f flv "rtmp://155484.livepush.myqcloud.com/live_appnm1/strm_nm?txSecret=13e0506e53634532d2c2686867d39e4b&txTime=61CE8FBE"

批处理特殊字符参数，使用双引号抱起来

D:\ffmpegbin\ffmpeg.exe -re -i d:/ccc/a.mp4 -f flv "rtmp://155484.livepush.myqcloud.com/live_appnm1/strm_nm?txSecret=13e0506e53634532d2c2686867d39e4b&txTime=61CE8FBE"


D:\ffmpegbin\ffmpeg.exe -re -i d:/ccc/a.mp4 -f flv "rtmp://155484.livepush.myqcloud.com/live_appnm1/strm_nm?txSecret=13e0506e53634532d2c2686867d39e4b&txTime=61CE8FBE"



D:\ffmpegbin\ffmpeg.exe -re -i d:/ccc/a.mp4 -f flv "rtmp://push.sunboyan.cn/live/strn1?txSecret=52cb37b394feb634e0d814618a52858e&txTime=61CE9AB8"

 

注意腾讯云测试的时候app和streamid名称要一直推拉六。。


7.ffmpeg本地视频推流测试
ffmpeg 推流地址：rtmp://127.0.0.1:1935/live/home
ffmpeg推流测试：ffmpeg.exe -re -i c:\ffmpeg\inputfile.mp4 -vcodec libx264 -acodec aac -f flv rtmp://127.0.0.1:1935/live/home 
ffmpeg 拉流测试：ffplay.exe rtmp://localhost:1935/live/home

摄像头推流

 摄像头推流测试
摄像头推流
ffmpeg -f dshow -i video="USB2.0 PC CAMERA" -vcodec libx264 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://127.0.0.1:1935/live/home
麦克风推流
ffmpeg -f dshow -i audio="麦克风 (2- USB2.0 MIC)" -vcodec libx264 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://127.0.0.1:1935/live/123
摄像头&麦克风推流
ffmpeg -f dshow -i video="USB2.0 PC CAMERA" -f dshow -i audio="麦克风 (2- USB2.0 MIC)" -vcodec libx264 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://127.0.0.1:1935/live/123
或者
ffmpeg -f dshow -i video="USB2.0 PC CAMERA":audio="麦克风 (2- USB2.0 MIC)" -vcodec libx264 -r 25 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://127.0.0.1:1935/live/123
屏幕推流
首先需要安装一个软件,screen capture recorder
编译好的下载地址是：http://sourceforge.net
屏幕推流
ffmpeg -f gdigrab -i desktop -vcodec libx264 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://127.0.0.1:1935/live/home
屏幕&麦克风推流
ffmpeg -f gdigrab -i "1:0" -vcodec libx264 -preset ultrafast -acodec libmp3lame -ar 44100 -ac 1 -f flv rtmp://127.0.0.1:1935/rtmplive/home
屏幕&麦克风&摄像头
ffmpeg -f avfoundation -framerate 30 -i "1:0" \-f avfoundation -framerate 30 -video_size 640x480 -i "0" \-c:v libx264 -preset ultrafast \-filter_complex 'overlay=main_w-overlay_w-10:main_h-overlay_h-10' -acodec libmp3lame -ar 44100 -ac 1 -f flv rtmp://localhost:1935/rtmplive/home

