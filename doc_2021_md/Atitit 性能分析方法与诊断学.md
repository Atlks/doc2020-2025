Atitit 性能分析方法与诊断学



 先将app和db分开，分别测试，得到性能瓶颈是在db还是在web app


可以使用编程语言  profile工具记录性能日记。。然后使用gui工具分析。。


性能跟踪工具又叫profile工具
paip.提升性能---软件的性能跟踪java .net php c++最佳实践.

软件的性能跟踪工具又叫profile工具.主要用来俩个方面
1.对象,变量的内存使用状态
2.方法的执行时间跟踪.


Java profile

Atitit 软件问题诊断学


目录
1. 第一篇 常见症状 	1
1.1. 性能 可读性 开发效率 扩展性 稳定性	1
1.2. 安全性	1
2. 第二篇 问诊 	2
3. 检查	2
3.1. 第一节 视诊 静态试诊断	2
3.2. 	2
4. 第四篇 实验诊断  	2
4.1. 运行诊断	2
4.2. 日志诊断	2
4.3. 单元测试	2
5. 	2
6. 第五篇 辅助检查  	2
7. 第六篇 病历书写  	2
8. 第七篇 诊断故障的步骤和思维方法	3
8.1.   	3



Php的profile


Atitit php性能诊断分析与提升方法与工具

先将app和db分开，分别测试，得到性能瓶颈是在db还是在web app


可以使用php xdebug profile工具记录性能日记。。然后使用gui工具分析。。
将以上文件拷贝到Windows上，用客户端软件WinCacheGrind打开每个文件，发现以下PHP程序执行所耗费的时间最长：
在优化php代码执行效率的过程中，有个好办法是利用XDebug或XHProf生成Profile文件，然后查看Profile文件分析整个程序的瓶颈在哪里。如果用XDebug生成Profile文件，方法参见前面的文章学习使用XDebug. 现在XDebug Profile的查看程序有好几个，在这里罗列一下：

WinCacheGrind
    WinCacheGrind是windows下的profile查看程序，使用起来感觉还不错，profile文件太大的话偶尔会崩溃。

Python profile
paip.性能跟踪profile原理与架构与本质-- ython扫带java php 

Ref

paip.提升性能---软件的性能跟踪java .net php c++最佳实践.


