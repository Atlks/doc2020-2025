Atitit NoClassDefFoundError


手动加载到build目录里面去不行，，放入tomcat web-info/lib也找不到。。

只好让如jdk、ext ，这时候就找到了。。可以debug启动了。。。
如果还不行，那么可能就是tomcat使用对是jdk下面对jre不是安装对jre，在正确对jer lib下面放入spring bean jar就可以了。。

Atitit tomcat debug启动nitializing c3p0 pool... com.mchange.v2.c3p0.ComboPooledDataSource 启动卡住

