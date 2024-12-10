Attit 数据库诊断问题工具


单元测试。。。Jvisual查看线程。。。Jdbc可执行sql打印

优化工具有啥
数据库层面
检查问题常用的 12 个工具：

MySQL


mysqladmin：MySQL 客户端，可进行管理操作


mysqlshow：功能强大的查看 shell 命令


SHOW [SESSION | GLOBAL] variables：查看数据库参数信息


SHOW [SESSION | GLOBAL] STATUS：查看数据库的状态信息


information_schema：获取元数据的方法


SHOW ENGINE INNODB STATUS：Innodb 引擎的所有状态


SHOW PROCESSLIST：查看当前所有连接的 session 状态


explain：获取查询语句的执行计划


show index：查看表的索引信息


slow-log：记录慢查询语句


mysqldumpslow：分析 slowlog 文件的工具





数据库层面问题解决思路
一般应急调优的思路：针对突然的业务办理卡顿，无法进行正常的业务处理，需要马上解决的场景。

1、show processlist


2、explain  select id ,name from stu where name='clsn'; # ALL  id name age  sex


            select id,name from stu  where id=2-1 函数 结果集>30;


　　　 show index from table;


3、通过执行计划判断，索引问题（有没有、合不合理）或者语句本身问题


4、show status  like '%lock%';    # 查询锁状态


　　kill SESSION_ID;   # 杀掉有问题的session

常规调优思路：针对业务周期性的卡顿，例如在每天 10-11 点业务特别慢，但是还能够使用，过了这段时间就好了。

1）查看slowlog，分析slowlog，分析出查询慢的语句；


2）按照一定优先级，一个一个排查所有慢语句；


3）分析top SQL，进行explain调试，查看语句执行时间；


4）调整索引或语句本身。





