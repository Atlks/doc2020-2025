Atitit php性能诊断分析与提升方法与工具

先将app和db分开，分别测试，得到性能瓶颈是在db还是在web app


可以使用php xdebug profile工具记录性能日记。。然后使用gui工具分析。。
将以上文件拷贝到Windows上，用客户端软件WinCacheGrind打开每个文件，发现以下PHP程序执行所耗费的时间最长：


paip.性能跟踪profile原理与架构与本质-- ython扫带java php 
