Atitit 提升稳定性 定时任务kill



*/30 * * * * ps -ef | grep java | grep -v grep | awk '{print $2}' | xargs kill -9


Linux 杀掉所有Java进程

yayaqwl 2018-04-01 21:38:31  7128  收藏 1
展开
1.   Linux查看所有Java进程

ps -ef | grep java | grep -v grep 

(是在列出的进程中去除含有关键字"grep"的进程)

2. 使用awk分割结果，获取PID

awk '{print $2}'

ps -ef | grep java | grep -v grep | awk '{print $2}'

3. 杀死进程 kill -9 PID

xargs 作用是将参数列表转换成小块分段传递给其他命令，以避免参数列表过长的问题

ps -ef | grep java | grep -v grep | awk '{print $2}' | xargs kill -9

具体xargs的用法请查看https://blog.csdn.net/u011517841/article/details/53196380
————————————————
版权声明：本文为CSDN博主「yayaqwl」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u011517841/article/details/79781830  
