Atitit.wmic接口

，通过使用WMI我们可以获取服务器硬件信息、收集服务器性能数据、操作Windows服务，甚至可以远程关机或是重启服务器。 
先决条件：
a. 启动Windows Management Instrumentation服务，开放TCP135端口。
b. 本地安全策略的“网络访问: 本地帐户的共享和安全模式”应设为“经典-本地用户以自己的身份验证”。

1. wmic /node:"192.168.1.20" /user:"domain\administrator" /password:"123456"
【硬件管理】：
1. wmic /node:"192.168.1.20" /user:"domain\administrator" /password:"123456"
3. PROCESS【进程管理】：
3. USERACCOUNT【账号管理】：
4. SHARE【共享管理】：
5. SERVICE【服务管理】：
6. FSDIR【目录管理】
7.datafile【文件管理】
8.【任务计划】：


比CMD更强大的命令行WMIC - 与时俱进 - 博客园.html


