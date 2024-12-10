Atitt 黑客技术获取信息 本机信息 网路信息 网路other dvc info..fish info

Huoqu pc name

wmic desktopmonitor



C:\Users\ati>systeminfo

主机名:           PC-FH-ATI
OS 名称:          Microsoft Windows 10 专业教育版
OS 版本:          10.0.19042 暂缺 Build 19042
OS 制造商:        Microsoft Corporation
OS 配置:          独立工作站
OS 构建类型:      Multiprocessor Free
注册的所有人:     User
注册的组织:
产品 ID:          00378-40000-00001-AA323
初始安装日期:     23/07/2021, 7:21:36 am
系统启动时间:     18/12/2021, 1:13:21 am
系统制造商:       Micro-Star International Co., Ltd.
系统型号:         GL62M 7RDX
处理器:           安装了 1 个处理器。
                  [01]: Intel64 Family 6 Model 158 Stepping 9 GenuineIntel ~2801 Mhz
BIOS 版本:        American Megatrends Inc. E16J9IMS.31A, 11/07/2017
Windows 目录:     C:\WINDOWS
系统目录:         C:\WINDOWS\system32
启动设备:         \Device\HarddiskVolume3
系统区域设置:     zh-cn;中文(中国)
输入法区域设置:   zh-cn;中文(中国)
时区:             (UTC+08:00) 北京，重庆，香港特别行政区，乌鲁木齐
物理内存总量:     16,304 MB
可用的物理内存:   1,274 MB

获取cpu mem信息


获取显示器信息
wmic path win32_desktopmonitor get /format:list
根据笔记本型号去网站查询。。
冒失wmic里面没有，只能通过读取注册表里面的通过读取注册表可以获取到显示器信息

通过分辨率计算。。
   1080          1920
PixelsPerXLogicalInch    120
1080/120=9inch
1920/120=16inch、41cm..  对角线长度=18inch？？

长宽分别为 
可以看到有屏幕分辨率和 PPI，但是这里的PPI只是一个逻辑尺寸上的PPI，并不准确，
而且貌似在WIN10上并不会显示屏幕分辩率，所以这种方法不可用。

Windows下用Python获取电脑显示器物理尺寸和PPI_Rdryma的博客-CSDN博客_python获取屏幕尺寸
ms-access - 如何获得显示器尺寸 - IT工具网


根据注册表查询笔记准确

这里我们可以得到显示器的实际尺寸，推荐（最大）分辩率，从而计算出PPI。
但是这里有一个问题，注册表中有时候会包含好几个显示器的信息（
Windows下用Python获取电脑显示器物理尺寸和PPI_Rdryma的博客-CSDN博客_python获取屏幕尺寸

可以根据wmic得到屏幕尺寸

C:\Users\ati>wmic /namespace:\\ROOT\WMI path WmiMonitorListedSupportedSourceModes get MonitorSourceModes /format:list


HorizontalImageSize=344  ，13.54inch   x2=183.4
VerticalImageSize=193     7.6 inch   x2=57.7
X2+x2///gegnhao2=15.5inch...
2、查看系统信息：systeminfo
3、查询BIOS详细信息：wmic bios
4、查看CPU详细信息：wmic cpu
5、查看CPU型号：wmic cpu list brief
6、查看内存详细信息：wmic memorychip
7、查看内存条数：wmic memorychip list brief
8、查看缓存内存：wmic memcache list brief
9、查看磁盘详细信息：wmic diskdrive
 磁盘信息
wmic diskdrive get model,interfacetype,size,totalsectors,partitions | findstr ".*"

分区信息
wmic logicaldisk get Caption,FileSystem,FreeSpace,Size |findstr -v "X:"

硬盘信息
wmic diskdrive get model^,interfacetype^,size^,totalsectors^,partitions/value


★结尾
有些硬件没有数字化的信息或其它原因，所以系统不能采集这些硬件的信息，例如：电源、键盘、鼠标、音箱、机箱和散热器

