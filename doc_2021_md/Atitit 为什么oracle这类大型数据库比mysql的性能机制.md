Atitit 为什么oracle这类大型数据库比mysql的性能机制

分区机制差别


Join算法

ForceIndex/Use Index
支持
支持
Oracle hints


join算法
hash join
不支持
支持
MySQL只有普通的嵌套循环算法
merge join
不支持
支持

Sql语句性能与trigger
触发器
DDL触发器
不支持
完美支持
MySQL不支持DDL触发器。Oracle支持基于DDL的触发器。
行触发器
支持
支持
MySQL不能在触发器里面取消对表的更改。Oracle可以在触发器里面取消对表的更改操作
语句触发器
不支持
支持
MySQL不支持。Oracle支持基于基于语句的触发器
触发器合并
不支持
支持
Oracle支持多个触发器合并。


Io机制
表与索引空间相互分离

表空间
数据库空间
不支持
支持
MySQL只有针对表的表空间，没有针对数据库的表空间。Oracle 有单独的数据库空间。
索引空间
不支持
支持
MySQL的数据以及索引都是放在单独的文件里面。Oracle 有针对专门针对索引的空间。
临时表空间
支持
支持
MySQL5.7 支持临时表空间
堆表与索引组织表的的对比

Oracle支持堆表，也支持索引组织表
PostgreSQL只支持堆表，不支持索引组织表
Innodb只支持索引组织表


Cache
物化视图oracle支持

Query cache
多核支持
Oracle进程模式与mysql线程模式的对比

PostgreSQL和oracle是进程模式，MySQL是线程模式。
进程模式对多CPU利用率比较高。
进程模式共享数据需要用到共享内存，而线程模式数据本身就是在进程空间内都是共享的，不同线程访问只需要控制好线程之间的同步。
线程模式对资源消耗比较少。
所以MySQL能支持远比oracle多的更多的连接。

多核支持oracle更好
多核并行查询一条sql oracle支持，mysql不支持

索引机制
Hash索引 mysql仅仅支持mem存储引擎加hash索引
大数据量下bree要查询三四层，三四次io。。
Hash只需要一次
降序索引反向索引
索引聚簇表


函数索引

同硬件情况与mysql性能对比

结论
补充
对Mysql的doublewrite关闭后进行了性能测试，并没有对数据有多大影响；
Ref
Atitit 数据库对比较 oracle  mysql pgsql

数据库对比 | MySQL vs Oracle - 墨天轮
