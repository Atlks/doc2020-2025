Atitit 未来数据库新特性展望

统一的翻页
2 Easy Top-N and pagination queries 更易用的Top-N和页码查询
1.2. 新的分页查询语法。offset和fetch 1
窗口函数
语言扩展

2. 语言扩展
除了用 R 和 Python 编写的代码外，开发人员现在还可以在 SQL Server 脚本和存储过程中执行 Java 代码
Java php python js扩展sp udf等

半结构化数据类型 Json数据类型 xml等
Table Value Parameters 
– 在许多客户的场景中，要传递一个表结构的值(行)的集合到服务器上的一个存储过程或函数中。这些值可能直接用于插入表或更新表，或者是用于更复杂的数据操作


Json函数

Oo类型

User自定义类型
讨论PostgreSQL 和其他数据库的差异在哪里-聚能聊-云栖社区.html



继承
PostgreSQL实现了表继承，这个特性对数据库设计人员来说是一个很有效的工具。 SQL99及以后的标准定义了类型继承特性，和我们在这里描述的很多特性有区别。
让我们从一个例子开始：假设我们试图制作一个城市数据模型。每个州都有许多城市，但是只有一个首府。 我们希望能够迅速检索任何州的首府。这个任务可以通过创建两个表来实现，一个是州府表，一个是非州府表。 不过，如果我们不管什么城市都想查该怎么办?继承的特性可以帮助我们解决这个问题。 我们定义capitals 表，它继承自cities表：

表继承
2. 持久化内存存储支持 - Persistent Memory Store
3. SQL的宏支持 - SQL Macro
机器学习算法和AutoML支持
4.自动化索引创建和实施	6
Es就有自动化索引，但插入性能太低。。
或者更加智能些，根据wehre语句自动构建
5.近似查询 - Approximate Query 和 Top-N 近似聚合	6


5.4. 系统字段
每个表都有几个系统字段 ，这些字段是由系统隐含定义的。 因此，这些名字不能用于用户定义的字段名。请注意这些限制与这个名字是否关 键字无关，把名字用引号括起来并不能让你逃离这些限制。你实际上不需要注意 这些字段，只要知道它们存在就可以了。
oid
行对象标识符(对象ID)。这个字段只有在创建表的时候使用了WITH OIDS 或者是配置参数default_with_oids的值为真时出现。 这个字段的类型是oid(和字段同名)。 参阅Section 8.16获取有关这种类型的更多信息。
tableoid
包含本行的表的OID。这个字段对那些从继承层次中选取的查询特别有用 (参阅节Section 5.8)，因为如果没有它的话，我们就很难 说明一行来自哪个独立的表。tableoid可以 和pg_class的oid 字段连接起来获取表名字。
xmin
插入该行版本的事务标识(事务ID)。注意：在这个环境里，一个行版本是一行的 一个状态；一行的每次更新都为同一个逻辑行创建一个新的行版本。
cmin
在插入事务内部的命令标识(从零开始)。
xmax
删除事务的标识(事务ID)，如果不是被删除的行版本，那么是零。在一个可见行版本里， 这个字段有可能是非零。这通常意味着删除事务还没有提交，或者是一个删除的企图被回滚掉了。
cmax
删除事务内部的命令标识符，或者是零。
ctid
一个行版本在它所处的表内的物理位置。请注意，尽管ctid 可以用于非常快速地定位行版本，但每次VACUUM FULL之后， 一个行的ctid都会被更新或者移动。因此ctid是不能作为长期的行标识符的。应该使用 OID ， 或者更好是用户定义的序列号，来标识一个逻辑行。

Updttime  inserttime updator  insertor

Ver
Other
4. try ... catch 支持
5. 通用表达式CTE ...可以在语句中返回一个结果集的通用表表达式(CTEs)
6. 直接发布Web Service 
7.CLR支持:这一点让你可以在数据库管理系统中执行.NET代码以充分利用.NET功能。它有望在SQL Server 2000环境中取代扩展的存储过程
8.SMTP邮件
Ref

Atitit.数据库新特性mssql sqlserver  SQL2014 sql2016 mssql2019 v3 u00.docx
Atitit.数据库新特性mssql sqlserver 2008 SQL2012 SQL2014 sql2016 v2 s22.docx
Atitit.数据库新特性mssql sqlserver 2008 SQL2012 SQL2014 sql2016
1. Mssql 2019 新特性	2
2. 语言扩展	2
2. SQL Server 2016最值得关注的10大新特性 - 51CTO.COM.html	2
2.1. JSON支持	2
3. Sql2014 新特性	3
3.2. 	3
3.3. 内存数据库 In-Memory OLTP不同之处	3
3.4. 1.利用SSD对高使用频率数据进行缓存处理	3
3.5. 全新行存储	3
3.6. BI：	4
3.7. 其他	4
4. 参考	5
5. 1. Sql2012 新特性 1	5
6. SQL2005新特性  (体积应该在800M左右)	6
6.1. 1. TOP 表达式	7
6.2. 2.between分页 where row between 20 and 30.....一句话就支持分页	7
6.3. 4. try ... catch 支持	7
6.4. 5. 通用表达式CTE ...可以在语句中返回一个结果集的通用表表达式(CTEs)	7
6.5. 6. 直接发布Web Service	7
6.6. 7.CLR支持:这一点让你可以在数据库管理系统中执行.NET代码以充分利用.NET功能。它有望在SQL Server 2000环境中取代扩展的存储过程	7
6.7. 8.SMTP邮件	7
7. SQL2008新特性  (体积1.5G左右.)	8
7.1. 4.全文检索	8
7.2. 5.MERGESQL语句	8
7.3. 6.Microsoft Office渲染	9
7.4. Table Value Parameters	9
8. sql2008 r2 (1.5G左右)	10
9. SQL2012 新特性  (体积1.6G,X86版)	11
9.1. 2.　Fetch与Offset 分页	11
9.2. 3.T-SQL从2005年就开始支持TRY-CATCH ，但奇怪的是，直到现在才有了THROW。	11
9.3. 4.EOMONTH函数用于返回月份的最后一天，这对报表是一个非常有用的特性	11
10. -----------------------EXPRESS版本比较	12
11. 参考	14
12. 参考资料	14
12.1. Atitit.数据库新特性战略规划mssqlsqlserver2008SQL2012SQL2014 - SQL Server(mssql)数据库栏目 - 红黑联盟.html	14



Atitit oracle新特性 18 19c 20c v2 u06.docx
Atitit oracle新特性  11 12  13 14 15 v1 u66.docx
Atitit oracle新特性5 6 7 8 9 10 11 12 18 19 20 attilax总结

目录
1.1. :ora 20c	1
1.2. Oracle Database 19c 的10大新特性早知道	3	1
1.3. Oracle Database 18c 的10大新特性一览	3	2
1.4.  只听过8i/9i/10g/11g/12c i 表示internet g 表示grid c 表示cloud	2
1.5. Ora 13-17 cant find	3
1.6. Oracle 11  12	3
2. eref	4

