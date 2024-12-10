使用FFMpeg从mp4中提取mp3

weixin_43822111 2021-05-10 16:39:26  234  收藏 1
分类专栏： 音视频 文章标签： ffmpeg
版权

音视频
专栏收录该内容
1 篇文章0 订阅
订阅专栏
在ffmpeg的bin目录下放置xxx.mp4文件，并进入cmd命令行。
输入命令：ffmpeg.exe -i xxx.mp4 -f mp3 -vn xxx.mp3并回车。
参数解释：-i表示input，-f表示format，-vn表示video not
————————————————
D:\ffmpegbin\ffmpeg.exe -i D:\Bumpy Ride.mp4 -f mp3 -vn  bumpy_ride.mp3
D:\ffmpegbin\ffmpeg.exe -i "D:\Bumpy Ride.mp4" -f mp3 -vn  bumpy_ride.mp3

D:\ffmpegbin\ffmpeg.exe -i "D:\Downloads\Nu Virgos - Stop Stop Stop.mp4" -f mp3 -vn  “Nu Virgos - Stop Stop Stop.mp3”

D:\ffmpegbin\ffmpeg.exe -i "D:\Downloads\sweetbox china girl.mp4" -f mp3 -vn  “sweetbox china girl.mp3”
D:\ffmpegbin\ffmpeg.exe -i "D:\ccc\Multicyde - A Better Day (1).flac" -ab 320k -map_metadata 0 -id3v2_version 3 "Multicyde - A Better Day.mp3"
sweetbox china girl.mp4


D:\ffmpegbin\ffmpeg.exe -i "D:\user\ati\OneDrive\Documents\music lisaigao\mp4\vejyo.mp4"  -acodec copy -vn  “vejyo.mp3”
Invaild audio fmt
D:\ffmpegbin\ffmpeg.exe -i "D:\user\ati\OneDrive\Documents\music lisaigao\mp4\vejyo.mp4"  -f mp3 -ab 320k -vn  “vejyo.mp3”

D:\ffmpegbin\ffmpeg.exe -i "D:\user\ati\OneDrive\Documents\music lisaigao\mp4\vejyo2.mp4"  -f mp3 -ab 320k -vn  “vejyo 37s.mp3”


D:\ffmpegbin\ffmpeg.exe -i "D:\user\ati\OneDrive\Documents\music lisaigao\mp4\tasehae .mp4"  -f mp3 -ab 320k -vn  “tasehae .mp3”

其他操作[4]
1.分离视频音频流
ffmpeg -i input_file -vcodec copy -an output_file_video　　//分离视频流
ffmpeg -i input_file -acodec copy -vn output_file_audio　　//分离音频流

