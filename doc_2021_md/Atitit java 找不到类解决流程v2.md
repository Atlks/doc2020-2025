Atitit java 找不到类解决流程
.NoClassDefFoundError: org.springframework.beans.FatalBeanException
class文件加入到启动配置cp
使用everything查看是否有clas文件。。
将class文件加入到启动配置cp路径里面去。。



Problem不对，可能是class文件过久，删除重编译

删除cls，重新编译。。
重新改动下文件，触发新编译。。
Builder、clr重新编译


没能重新编译对解决
重新改动下文件，触发新编译。。
Builder、clr重新编译

将jar放入jdk  lib路径  放入buld路径
可能是动态加载class太多导致加载不来，调整xss xmx参数
