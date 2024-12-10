Atititi tesseract使用总结
\


项目下载地址为 https://github.com/tesseract-ocr/

消除bug，优化，重新发布。当前版本为3.02
项目下载地址为：http://code.google.com/p/tesseract-ocr。


 
Windows cmd命令行使用Tesseract-OCR引擎识别验证码:
1、下载安装Tesseract-OCR引擎(3.0版本+才支持中文识别)
 tesseract-ocr-setup-3.01-1.exe.
下载完后进行安装,默认情况下安装程序会给你配置系统环境变量,以指向安装目录（之后可以通过DOS界面在任意目录运行tesseract）。安装完成后目录如下:

语言的字库文件
https://github.com/tesseract-ocr/

tessdata 目录存放的是语言字库文件，和在命令行界面中可能用到的参数所对应的文件. 这个安装程序默认包含了英文字库。
如果想能识别中文，可以到http://code.google.com/p/tesseract-ocr/downloads/list下载对应的语言的字库文件.
简体中文字库文件下载地址为:http://tesseract-ocr.googlecode.com/files/chi_sim.traineddata.gz下载完成后解压，然后将该文件剪切到tessdata目录下去就可以了。



附录:
Usage:tesseract imagename outputbase [-l lang] [-psm pagesegmode] [configfile...]
pagesegmode values are:
0 = Orientation and script detection (OSD) only.
1 = Automatic page segmentation with OSD.
2 = Automatic page segmentation, but no OSD, or OCR
3 = Fully automatic page segmentation, but no OSD. (Default)
4 = Assume a single column of text of variable sizes.
5 = Assume a single uniform block of vertically aligned text.
6 = Assume a single uniform block of text.
7 = Treat the image as a single text line.
8 = Treat the image as a single word.
9 = Treat the image as a single word in a circle.
10 = Treat the image as a single character.
-l lang and/or -psm pagesegmode must occur before anyconfigfile.

tesseract imagename outputbase [-l lang] [-psm pagesegmode] [configfile...]
tesseract 图片名 输出文件名 -l 字库文件 -psm pagesegmode 配置文件
例如：
tesseract code.jpg result -l chi_sim -psm 7 nobatch
-l chi_sim 表示用简体中文字库（需要下载中文字库文件，解压后，存放到tessdata目录下去,字库文件扩展名为 .raineddata 简体中文字库文件名为: chi_sim.traineddata）
-psm 7 表示告诉tesseract code.jpg图片是一行文本 这个参数可以减少识别错误率. 默认为 3
configfile 参数值为tessdata\configs 和 tessdata\tessconfigs 目录下的文件名.


tesseract.exe C:\0prj\ocrtest.jpg   C:\0prj\ocrout\ocrtest -l chi_sim


"C:\0workspace\Tesseract\tesseract.exe"  "D:\ati\dcim_mov22\IMG_0177.PNG" "D:\ati\dcim_mov22\IMG_0177" 
cmd ext finish!
““- 中国联通 一÷、 1:36 AM @ 4 >B 64%庄〕
wapbaike.baidu.com
那样既闷热又不方便, 所以文暴走们就用书包代替保护
颈椎的护具, 不过这些书包少的几十, 贵的几百上干还
可以放东西真是一举两得。 不过可不要因此认为他们很
温柔, 和这些文暴走比速度, 因为在他们眼里就算兰博
墓启都只有屹灰的份。 排量 干以上的机车〇-wO提速
足以秒杀布加迪威龙以下的汽车, 也许正是因为这种对
提速的迷恋才是他们热爱机车的原因! 发展到今夭, 文
暴走里面又衍生出了炸街党。 田于对社会压力的释放已
不能通过飙车来满足, 文暴走们不再低调, 换掉原装排
气的重型机车, 咆哮的声音足够让整个市中心知道他的
存在。 在车流中的浑厚引擎声, 仿佛告诉人们, 生活中
你不在沉默中死亡, 就在沉默中胞晖, 他们正是这群沉
默的胞晖耆。 行云流水般的车技, 加上轰炸式的声音,
也就行成了炸街一词。 用咆晖的引擎让整条街的玻璃和
地板都为之震动, 百分之百的回头率, 告诉着你, 胯下
的巨物可不是闹着玩的, 它身价不菲, 同样它藐视所有
法则, 因为跨上去的那一刻, 就与世界脱离, 告诉你这
是 群有故事的人。
历史起源
硼 个
说起日本的暴走族% 就不能不提到广岛, 因加Ba
走凤气最盛行, 被日本媒体称为“广岛现象% 这认 ,、
走风’再次刮起, 广岛自然不甘落后。 -个朋友告诉笔
耆, 最近几夭, 他时常看到马力强劲的摩托车在广岛街

要不要转换tif,attilax测试,是一样的效果....

Java调用OCR进行图片识别 - conanswp的专栏 - 博客频道 - CSDN.NET.html

 Atiend

