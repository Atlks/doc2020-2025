Atitit mybatis 调试系列 查看具体执行sql


方案1： 
网上说的比较多的，之前也是这么用的一种方式 
1:首先将ibatis log4j运行级别调到DEBUG可以在控制台打印出ibatis运行的sql语句 
2:添加如下语句

###显示SQL语句部分


log4j.logger.com.ibatis=DEBUG


log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=DEBUG


log4j.logger.com.ibatis.common.jdbc.ScriptRunner=DEBUG


log4j.logger.com.ibatis.sqlmap.engine.impl.SqlMapClientDelegate=DEBUG


log4j.logger.Java.sql.Connection=DEBUG


log4j.logger.java.sql.Statement=DEBUG


log4j.logger.java.sql.PreparedStatement=DEBUG

方案2： 
最近发现的一种方式，方便快捷 
在mybatis.cfg.xml中增加如下配置

<settings>中增加


<setting name="logImpl" value="STDOUT_LOGGING" />



