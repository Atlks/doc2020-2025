Atitit SQL调试获取可执行sql 真实sql


performance_schema


通常在java项目开发为了防止sql注入我们通常都采用的预编译的sql，采用“?”号挂参，如下：
SELECT * FROM blog WHERE id = ?
往往在开发测试阶段能获取到完整的可执行的sql能帮我们及时的发现和定位问题。就有了很多朋友使用log4jdbc来记录SQL信息
Druid搭配log4j2输出SQL语句和结果
一、引言
其实Druid的内置了log4jdbc来显示SQL语句，虽然显示效果不如原生的log4jdbc效果好，但是因为内置所以不需要其他更多的配置。
二、使


注意日志级别
注意一下 LoggerName 的 日志级别要设置为 Debug
如何获取可执行SQL
JDK 中 JDBC 规范只提供接口（如 PreparedStatement 接口），并未提供获取可执行SQL的接口
JDBC 规范的实现由各大数据库厂商实现，包括 预查询语句的 SQL 拼接 可执行语句也是由各大厂商实现
Druid 实现方式
Druid 自己实现了 PreparedStatement 参数的拼接
Druid 打印可执行 SQL | Mr.Kail's Blog


一、log4jdbc简单介绍:
log4jdbc是工作在jdbc层的一个日志框架，能够记录SQL及数据库连接执行信息。
一般的SQL日志会把占位符和参数值分开打印，log4jdbc则会记录数据库执行的完整SQL字符串，在数据库应用开发调试阶段非常有用。
log4jdbc具有以下特性：
支持JDBC3和JDBC4。
支持现有大部分JDBC驱动。
易于配置（在大部分情况下，只需要改变驱动类名和jdbc的URL，设置好日志输出级别）。
能够自动把SQL变量值加到SQL输出日志中，改进易读性和方便调试。
能够快速标识出应用程序中执行比较慢的SQL语句。
能够生成SQL连接数信息帮助识别连接池/线程问题。
1.依赖配置：
　　log4jdbc的使用需要依赖于log4j-1.2.17.jar、slf4j-api.jar-1.7.5、slf4j-log4j12-1.7.5.jar,然后下载log4jdbc-1.2.jar包
2.在日志配置文件中定义相关logger对象的输出级别和输出器：
　　在log4jdbc中定义了以下五个日志对象：
　　jdbc.sqlonly     : 记录系统执行过的sql语句
　　jdbc.sqltiming  : 记录sql执行的时间，可以分析耗时的sql语句
　　jdbc.audit        : 记录除了ResultSet外的所有JDBC调用情况。一般不需要。
　　jdbc.resultset   : 记录返回结果集信息
　　jdbc.connection: 记录数据库连接和释放信息，可记录当前的数据库连接数，便于诊断连接是否释放。

如果卡主，可能是filter名字没有写对啊


如果不能打印
可能是有多个log配置文件，看下其他配置文件里面有没有配置打印。。
Druid优先使用logback.xml，然后是log4j
可以在后面增加tag fromLogback or log4j区分哪里的配置

Druid 打印可执行 SQL | Mr.Kail's Blog
