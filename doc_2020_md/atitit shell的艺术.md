Aa

概念Shell vs core
 
（计算机壳层）
 编辑
在计算机科学中，Shell俗称壳（用来区别于核），是指“提供使用者使用界面”的软件（命令解析器）。它类似于DOS下的command.com和后来的cmd.exe。它接收用户命令，然后调用相应的应用程序。
由于操作系统是管理计算机系统硬件的核心，因此这个核心应该被保护，用户不能随随便便的对操作系统进行操作，因为不当的操作可能造成整个计算机硬件系统的崩溃。
          4.所以，就为操作系统做一层壳，来保护操作系统。而这层壳（Shell），是经过定义以及验证的，规定好的，用户的操作不会对计算机的硬件系统造成破坏。并且，通过Shell输入的命令，能够正确的被解析并传达到操作系统，而保证了相应的命令请求能够正确实施。
关系图：            

、 spawn 返回一个stream，exec返回一个buffer

 控制台console，标准输出stdin、stdout 以及错误输出


构成

NET Framework
Com  wsh wmi


基本上shell分两大类：
一：图形界面shell（Graphical User Interface shell 即 GUI shell）
例如：应用最为广泛的 Windows Explorer （微软的windows系列操作系统），还有也包括广为人知的 Linux shell，其中linux shell 包括 X window manager (BlackBox和FluxBox），以及功能更强大的CDE、GNOME、KDE、 XFCE。
二：命令行式shell（Command Line Interface shell ，即CLI shell）
其他分类
普通shell vs  powershell
Webshel vs 普通cs shell
更好的shell工具
 PowerShell
Wmic
Shell的编程环境
Java Runtime ProcessBulider 
Js  child_process').exec
Php  exec 
Net
常用shell功能
文件操作
进程管理
系统监控
系统配置
Other
实现自己的shell cli lib apache common cli
常见问题
管道解析，需要自己解析
编码问题
大文件缓冲问题
错误与正常输出转异常问题
timeout
Ref
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit  linux常用功能shell.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit java调用cmd shell 方法总结 Runtime ProcessBulider 命令行.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit java调用cmd shell 方法总结 Runtime ProcessBulider 命令行.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit linux运维shell脚本编写attilax总结.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit linux运维shell脚本编写attilax总结.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit mongodb shell.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit node.js 调用shell bat 批处理  api 最佳实践 命令行 v2 rb2.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit node.js 调用shell bat 批处理  api 最佳实践 命令行 v2 rb2.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit node.js 调用shell bat 批处理  api 最佳实践.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit shell 批处理循环目录 cli trave dir folder v2 s51.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit shell 批处理循环目录.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit 定时shell的编写attilax总结.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit 常用shell查找 进程打开端口号.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit 木马病毒webshell的原理and设计.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit 木马病毒webshell的原理and设计.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit.powershell中禁止执行脚本解决办法.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit.powershell中禁止执行脚本解决办法.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit.木马病毒webshell的原理and设计.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\atitit.木马病毒webshell的原理and设计.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit。动态调用java 语言作为脚本 beanshell.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitit。动态调用java 语言作为脚本 beanshell.docx.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\Atitti 根据端口号来守护 进程 shell bat脚本.docx
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017  r6 doc v2 raf、r6 r620 doc compc、0云印项目java部分的文档、Atitti 根据端口号来守护 进程 shell bat脚本.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017  r6 doc v2 raf、r65  data compc、005 r511、Atitit 定时shell的编写attilax总结.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017  r6 doc v2 raf、r65  data compc、005 r61、Atitti 根据端口号来守护 进程 shell bat脚本.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017 r5 doc v2 raf、Atitti 根据端口号来守护 进程 shell bat脚本.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017 r5 doc v2 raf、r65  data compc、005 r511、Atitit 定时shell的编写attilax总结.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r2017 r5 doc v2 raf、r65  data compc、005 r61、Atitti 根据端口号来守护 进程 shell bat脚本.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r3 doc list 4pub csdn、Atitit linux运维shell脚本编写attilax总结.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r3 doc、doc r310 com pc、Atitit linux运维shell脚本编写attilax总结.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\r3 doc、doc r310、Atitit linux运维shell脚本编写attilax总结.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\shell.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc 2005-1014、q4d、0up5 q311、atitit 木马病毒webshell的原理and设计.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc q2016、q1、q119U5、up5、Atitit。动态调用java 语言作为脚本 beanshell.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc q2016、q2F、q219、atitit.powershell中禁止执行脚本解决办法.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc q2016、q2、q219、atitit.powershell中禁止执行脚本解决办法.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc q2016、q3、q3f、0up5 q311、atitit.木马病毒webshell的原理and设计.docx.index.txt
C:\Users\Administrator\Desktop\shell pkgshell资料包\um doc q2016、q4、q4d、0up5 q311、atitit.木马病毒webshell的原理and设计.docx.index.txt


Shell maindchar

 1. 概念Shell vs core 1
1.1. （计算机壳层） 2
1.2. 、 spawn 返回一个stream，exec返回一个buffer  2
1.3. 控制台console
标准输出stdin、stdout 以及错误输出 2
5. 更好的shell工具 3
5.1.  PowerShell 3
5.2. Wmic 3
webshell
8. Other 3
8.1. 实现自己的shell cli
lib apache common cli 3
9. 常见问题 3
9.1. 管道解析，需要自己解析 3
9.2. 编码问题 4
9.3. 大文件缓冲问题 4
9.4. 错误与正常输出转异常问题 4
9.5. timeout 4
cwd curr work dir
特殊字符转义
内置命令解释 调用监视器
7. 常用shell功能 3
7.1. 文件操作 3
7.2. 进程管理 3
7.3. 系统监控 3
7.4. 系统配置 3
6. Shell的编程环境 3
6.1. Java Runtime
ProcessBulider 3
6.2. Js  child_process').exec 3
6.3. Php  exec 3
6.4. Net 3
attilax总结与s5g

