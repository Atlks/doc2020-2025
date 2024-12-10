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
