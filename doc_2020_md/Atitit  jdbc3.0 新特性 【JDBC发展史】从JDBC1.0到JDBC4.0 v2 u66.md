Atitit  jdbc3.0 新特性 【JDBC发展史】从JDBC1.0到JDBC4.0.html


jdbc2.0
1、一个java.sql.*包；
一个扩展包javax.sql.*包。

2、扩展包里有2个新增的技术，
1）数据源（DataSource）。
2）连接池（ConnectionPoolDataSource）。

四、JDBC 3.0
【更多：http://www.ibm.com/developerworks/cn/java/j-jdbcnew/】
JDBC3.0随JDK1.4一起发布，下面看看它的特性吧！
元数据 API
DatabaseMetaData 接口可以检索 SQL 类型的层次结构，一种新的 ParameterMetaData 接口可以描述 PreparedStatement 对象中参数的类型和属性。
CallableStatements 中已命名的参数
数据类型的改变  增加
JDBC 所支持的数据类型作了几个改变，其中之一是增加了两种新的数据类型。
增加的两种新的数据类型是 java.sql.Types.DATALINK 和 java.sql.Types.BOOLEAN。DATALINK 提供对外部资源的访问或 URL。DATALINK 列值是通过使用新的 getURL() 方法从 ResultSet 的一个实例中检索到的，
检索自动产生的关键字
为了解决对获取自动产生的或自动增加的关键字的值的需求，JDBC 3.0 API 现在将获取这种值变得很轻松。要确定任何所产生的关键字的值，只要简单地在语句的 execute() 方法中指定一个可选的标记，表示您有兴趣获取产生的值。您感兴趣的程度可以是 Statement.RETURN_GENERATED_KEYS ，也可以是 Statement.NO_GENERATED_KEYS 。在执行这条语句后
3、返回多重结果
4、在事务中使用 Savepoint
五.JDBC 4.0
6．对SQL XML的支持
自动加载驱动
Java.sql.DriverManager 的内部实现机制决定了这样代码的出现。只有先通过 Class.forName 找到特定驱动的 class 文件，DriverManager.getConnection 方法才能顺利地获得 Java 应用和数据库的连接。这样的代码为编写程序增加了不必要的负担，JDK 的开发者也意识到了这一点。从 Java 6 开始，应用程序不再需要显式地加载驱动程序了，DriverManager 开始能够自动地承担这项任务

SQLExcpetion 的增强
在 Java SE 6 之前，有关 JDBC 的异常类型不超过 10 个。这似乎已经不足以描述日渐复杂的数据库异常情况。因此，Java SE 6 的设计人员对以 java.sql.SQLException 为根的异常体系作了大幅度的改进。
ava 6 中新增的异常类被分为 3 种：SQLReoverableException、SQLNonTransientException、SQLTransientException。在 SQLNonTransientException 和 SQLTransientException 之下还有若干子类，详细地区分了 JDBC 程序中可能出现的各种错误情况。大多数子类都会有对应的标准 SQLState 值，很好地将 SQL 标准和 Java 6 类库结合在一起。

jdbc1.0、jdbc2.0、jdbc3.0、jdbc4.0的区别 - B_qxzb的专栏 - 博客频道 - CSDN.NET.html
(···条消息)JDBC 1.0 - 2.0 - 3.0 - 4.0简单比较_weixin_30247307的博客-CSDN博客
