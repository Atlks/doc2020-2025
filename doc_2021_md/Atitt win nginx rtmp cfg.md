Atitt win nginx rtmp cfg



Index of /download/
http://nginx-win.ecsds.eu › download

documentation-pdf/ 15-Mar-2018 20:00 - FAQ nginx-win version.txt ... 07-Nov-2021 11:51 3527190 nginx 1.7.11.3 Gryphon.zip 19-Mar-2015 20:51 2756798 nginx ...

Pre-compiled Windows version with RTMP (1.7.11.3 Gryphon)
https://www.reddit.com › nginx › comments › precomp...

26 Dec 2019 — Unfortunately, it looks like the source of the pre-compiled Windows version has recently removed the Gryphon build: http://nginx-win.ecsds.eu/download/.
Still looking for NGINX Gryphon.: thepiratebay - Reddit
2 Feb 2020
Pre-compiled Windows versions with rtmp? : r/nginx - Reddit
29 Oct 2016
More results from www.reddit.com




nginx: [emerg] unknown directive "rtmp" in 
5 nginx方式启动服务器（失败）
按住 windows 键 +R，输入 cmd，进入 cmd 命令窗口，进入 nginx 目录：cd E:\technology\nginx-1.17.9，然后启动 nginx rtmp 服务器：
nginx.exe -c conf\nginx-win.conf
出现该错误：
nginx: [emerg] unknown directive "rtmp" in E:\technology\nginx-1.17.9/conf\nginx-win.conf:19
网上搜索该错误，找到解决该问题的博客：windows下nginx的rtmp配置加载问题 unknown directive "rtmp"
原因是：nginx 的 windows 版本可能在编译的时候没有对 rtmp 模块进行编译导致使用不了。
方法1：
下载源码重新进行编译并把 rtmp 模块进行编译进去，过程较为繁琐，这里不推荐，有兴趣的可以参考：第二讲：win7下nginx-rtmp-module的编译方法
方法2：
下载带 rtmp 模块的 nginx 版本，如 nginx 1.7.11.3 Gryphon，后续亲测可用。



6 nginx Gryphon方式搭建RTMP服务器（成功）

一、nginx的安装和配置
    首先我们下载nginx。在nginx官网上下载的nginx是不带rtmp模块的，所以我们在http://nginx-win.ecsds.eu/download/中下载nginx 1.7.11.3 Gryphon.zip，如下图所示。该版本的nginx包含rtmp组件，通过rtmp组件，才能提供流媒体服务，使nginx成为rtmp流媒体服务器。

1. 下载 nginx 1.7.11.3 Gryphon
下载带 rtmp 模块的 nginx 版本，如 nginx 1.7.11.3 Gryphon，下载地址为：http://nginx-win.ecsds.eu/download/nginx
下载完成后解压，将解压后的目录名：nginx 1.7.11.3 Gryphon 改成：nginx-1.7.11.3-Gryphon。

关于使用FFmpeg推流时，live目录的理解
cuijiecheng2018 2019-11-16 00:02:14 1036 收藏 3
分类专栏： 音视频技术 文章标签： nginx 推流 ffmpeg
版权
音视频技术
专栏收录该内容
41 篇文章 4 订阅
订阅专栏

    根据博主之前的博文《在windows下搭建、配置nginx流媒体服务器，并进行rtmp流的推流、拉流测试》搭建好nginx流媒体服务器后，可能有些朋友会对博文里面进行推流测试的指令：“ ffmpeg -i video3.mp4 -f flv rtmp://127.0.0.1/live/test1 ”中的“ live ”有一些不理解。“ live ”其实是一个虚拟目录，这个目录和windows中传统的目录是不一样的，可以理解为推流到的流媒体服务器的模块路径或者虚拟路径，但是实际在流媒体服务器中是不会存在这个目录的，因为它是虚拟的。这个目录其实是用来区分流的，表示要推流到的地址；推流地址为多少，拉流地址就得为多少。比如推流指令为“ ffmpeg -i video3.mp4 -f flv rtmp://127.0.0.1/live/test1 ”，使用ffplay进行拉流的指令就得为“ ffplay rtmp://127.0.0.1/live/test1”，可以看到推流地址和拉流地址是对应的。

    在测试的过程中，可能有些朋友也会发现，将推流指令中的“ live ”目录改为其它目录时，推流会失败。比如在命令提示符中输入指令：“ ffmpeg -i video3.mp4 -f flv rtmp://127.0.0.1/mydir/test1 ”，推流会失败（但是输入指令“ ffmpeg -i video3.mp4 -f flv rtmp://127.0.0.1/live/test1 ”是可以成功进行推流的）如下图所示：
————————————————
题产生的原因是：推流目录其实是在nginx的配置文件中进行设置的，默认是“ live ”。在没有更改配置文件中推流目录的情况下改变指令中的推流目录，自然就会推流失败了。如下图所示，在nginx的conf目录下有配置文件nginx.conf。

打开该配置文件，我们可以看到有“ application live ”这一行内容。该行表示nginx的推流虚拟目录为“ live ”。所以我们的推流指令格式就只能为：ffmpeg -i “文件名” -f flv rtmp://“nginx所在电脑的IP地址”/live/“推流子目录”。
————————————————
 
