Atitit deploy prj部署项目总结

上传文件
Xshell zt
Xfalshftp等工具

增量部署
原理，比较修改过的文件，只更新修改过的文件


Git pull 拉取

Becompare 上传
Fx的比较不知道怎么样
后台运行
Java -jar xxx.jar
   java -cp D:/prj/sport-service/kok-sport-service/target/classes;D:/kok-sport-service-1.0-SNAPSHOT/BOOT-INF/lib/* com.kok.SportApplication
	  
 	  
	     nohup  java -cp /data/depl/target/classes:/data/depl/BOOT-INF/lib/* com.kok.SportApplication > SportApplication.log 2>&1 &
		 tail -f /data/depl/SportApplication.log
		 
热部署
实现无论修改class 还是xml文件均可立即生效无需重启服务

每次加载读取配置模式 （简单


Web服务器resin模式 （一般
Classload模式 （麻烦

运行文件
脚本类   php python node.js差不多
Java -cp classdir;jardir/*  pkg.classname   
Linujx 路径分隔用冒号，win分号
Sql文件   udf，读取file
运行代码片段 函数/语句
脚本类使用反射
Java可以使用spel spring
Mybatis xml 使用解析器udf（mapr.xml,statmentID)
服务端sql使用解析器 udf(sp,prms)

退出与重启服务
加个退出功能




