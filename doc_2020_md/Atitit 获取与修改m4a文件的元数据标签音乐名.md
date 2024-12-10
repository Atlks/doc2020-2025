Atitit 获取与修改m4a文件的元数据标签音乐名，歌手 专辑 年代等信息 java版本
方法一，使用cli工具类库获取mmpeg （推荐
ffmpeg.exe  -i  "C:\Users\Administrator\Music\-1106601338 huomyao - 副本.m4a"


C:\Users\Administrator>ffmpeg.exe  -i  "C:\Users\Administrator\Music\-1106601338 huomyao - 副本.m4a"
ffmpeg version 2.8.4 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 5.2.0 (GCC)
  configuration: --enable-gpl --enable-version3 --disable-w32threads --enable-avisynth --enable-bzlib --enable-fontconfig --enable-frei0r --enab
ray --enable-libbs2b --enable-libcaca --enable-libdcadec --enable-libfreetype --enable-libgme --enable-libgsm --enable-libilbc --enable-libmodpl
le-libopencore-amrwb --enable-libopenjpeg --enable-libopus --enable-librtmp --enable-libschroedinger --enable-libsoxr --enable-libspeex --enable
ble-libvo-aacenc --enable-libvo-amrwbenc --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx264 --enable-libx2
ble-decklink --enable-zlib
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'C:\Users\Administrator\Music\-1106601338 huomyao - 鍓湰.m4a':
  Metadata:
    major_brand     : M4A
    minor_version   : 0
    compatible_brands: M4A mp42isom
    creation_time   : 2018-05-13 09:11:53
    iTunSMPB        :  00000000 00000840 00000011 00000000008F47AF 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
    artist          : volin
    date            : 2018
    album           : homyao
    genre           : das
  Duration: 00:03:32.97, start: 0.000000, bitrate: 127 kb/s
    Stream #0:0(eng): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 125 kb/s (default)
    Metadata:
      creation_time   : 2018-05-13 09:11:53
At least one output file must be specified

使用jave类库，内部也是调用ffmpeg
自己解析mp4 m4a结构
使用图形化分析工具MP4Reader分析其ATOM/BOX结构


可以看到标签路径是 moov/udta/meta/ilst


