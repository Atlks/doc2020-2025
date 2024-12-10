Atitit SQL调试获取可执行sql 真实sql


也可以使用p6spy，它可以拦截所有执行的 SQL 语句
，而不管你使用的是什么 ORM 框架。对于 PrepareStatement 那样带参数(?) 的语句，它会帮你代上相应的参数值。 
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


一、log4jdbc简单介绍: tuijye
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
用法
将log4jdbc jar（基于JDK版本）放入应用程序的类路径中。
选择要使用的日志系统，支持log4j，logback，commons logging ..
在应用程序的配置中，将JDBC驱动程序类设置为net.sf.log4jdbc.DriverSpy。在许多情况下，被监视的基础驱动程序将自动加载，而无需任何其他配置。

将jdbc：log4前缀为您正在使用的普通jdbc url。

例如，如果您的常规jdbc网址是jdbc：derby：// localhost：1527 // db-derby-10.2.2.0-bin / databases / MyDatabase，那么您可以将其更改为：jdbc：log4jdbc：derby：// localhost： 1527 // db-derby-10.2.2.0-bin / databases / MyDatabase


设置您的记录器。

jdbc.sqlonly：仅记录SQL。在准备好的语句中执行的SQL会自动显示，其绑定参数替换为该位置上绑定的数据，从而大大提高了可读性。1.0

jdbc.sqltiming：在执行后记录SQL，包括有关执行SQL多长时间的计时统计信息。1.0

jdbc.audit：记录除结果集以外的所有JDBC调用。这是非常大量的输出，通常不需要，除非找到特定的JDBC问题。1.0

jdbc.resultset：更为庞大，因为记录了对ResultSet对象的所有调用。1.0

jdbc.connection：记录连接打开和关闭事件以及转储所有打开的连接号。这对于解决连接泄漏问题非常有用。


如果卡主，可能是filter名字没有写对啊


如果不能打印
可能是有多个log配置文件，看下其他配置文件里面有没有配置打印。。
Druid优先使用logback.xml，然后是log4j
可以在后面增加tag fromLogback or log4j区分哪里的配置
Other

9

如果您使用的是Spring框架，那么datasource-proxy框架将非常方便。您基本上可以包装任何东西，DataSource而只需添加日志记录行为。


开启mysql 等数据库驱动的debug设置

Druid 打印可执行 SQL | Mr.Kail's Blog
