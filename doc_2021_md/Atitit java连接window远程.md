Atitit java连接window远程


远程部署，都是用的powershellserver

Telnet+ftp

Ssh（通用，linux也用）

windows由于没有默认的ssh server，因此在允许ssh之前需要先安装ssh server。
下载freeSSHd
http://www.freesshd.com/?ctt=download
安装
直接执行freeSSHd.exe就可以进行安装了（用户一定要有管理员权限），安装过程中freeSSHd会问你
Private keys should be created. Should I do it now?
这是问你是否需要现在创建私钥，回答是
Do you want to run FreeSSHd as a system service?
这是问你是否希望把freeSSHd作为系统服务启动，回答是之后就安装完成了。
安装完成之后，双击freesshd图标（桌面或开始菜单），不会直接打开配置界面，而是需要在任务栏的“显示隐藏图标”（正三角图标）处右键freessh图标，选择setting。
配置用户名和密码：（java代码中连接的用户名和密码）

检查freesshd server status状态。切换至“server status”标签页，查看“SSH server is running”是否打钩，如果没有，点击下方连接检查，如果报错“the specified address is already in use”，则是由于安装时询问“Do you want to run FreeSSHd as a system service?”选择了“是”导致的，只需要在services.msc中将该服务停掉，再在配置界面启动，显示为打钩状态即可。

2017年1月22日 — freeSSHD在windows环境下搭建SFTP服务器0 建议现在windows环境下安装cygwin，否则在windows环境下cmd模式使用不了sftp去连接，可以


Tsclient

适当的JavaRDP

propertyJavaRDP是Windows终端服务的开源Java RDP客户端。它基于rdesktop（SourceForge项目）。properJavaRDP在Java 1.1以上版本（针对1.4进行了优化）上运行，并且在Linux， Windows和Mac上运行良好。它还包括log4j-java1.1，这是log4j的Java 1.1后端。
properJavaRDP是由Phil Carmalt和Tom Elliot在Propero Ltd上开发的，它们是按需框架的一部分，用于虚拟化应用程序交付。
properJavaRDP已获得GNU通用公共许可证（请参阅gpl.txt）的许可，并且不附带保修。
在哪里得到它
如何使用

wmi4j是纯Java实现的Windows WMI客户端

Java用wmi4j远程管理Windows 
wmi4j是纯Java实现的Windows WMI客户端，它基于j-interop针对WMI重新封装，提供了更便捷的方法，能满足基本的windows管理，包括服务管理，性能查询，执行脚本等等。
wmi4j下载
用Maven的朋友们可以直接引入，groupId=cn.chenlichao, artifactId=wmi4j, version=0.9。 源码地址: Github: https://github.com/chenlichao-cn/wmi4j使用其他构件框架的朋友，可以去maven中央库或者http://maven.oschina.net查询wmi4j，当然要记得下载它的依赖包：

org.glassfish.main.external:j-interop-repackaged:4.0


org.slf4j:slf4j-api:1.7.7


org.apache.commons:commons-lang3:3.1


