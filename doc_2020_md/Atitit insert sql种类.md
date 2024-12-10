Atitit insert sql种类


Insert的种类
普通insert
MERGE（融合）插入?
Select insert

语法原理

MERGE是Oracle9i新增的语法，用来合并UPDATE和INSERT语句
判断某个字段（主键，unique，或联合字段）是否重复


现状

MERGE语句是SQL语句的一种。在SQL Server、Oracle数据库中可用，MySQL、PostgreSQL中不可用。MERGE是Oracle9i新增的语法，用来合并UPDATE和INSERT语句。通过MERGE语句，根据一张表（原数据表，source table）或子查询的连接条件对另外一张（目标表，target table）表进行查询，连接条件匹配上的进行UPDATE，无法匹配的执行INSERT。这个语法仅需要一次全表扫描就完成了全部工作，执行效率要高于INSERT+UPDATE。

在Oracle 10g之前，merge语句支持匹配更新和不匹配插入两种简单的用法，在10g中Oracle对merge语句做了增强，增加了条件选项和DELETE操作。

Oracle语法

接下来要改成正确的语句就容易多了，如下：
MERGE INTO T T1
USING (SELECT '1001' AS a,2 AS b FROM dual) T2
ON ( T1.a=T2.a)
WHEN MATCHED THEN
  UPDATE SET T1.b = T2.b
WHEN NOT MATCHED THEN 
  INSERT (a,b) VALUES(T2.a,T2.b);

Mysql的实现

mysql的replace into命令
replace into的用法，真的很好用，是insert into的增强版。在向表中插入数据时，我们经常会遇到这样的情况：1、首先判断数据是否存在；2、如果不存在，则插入；3、如果存在，则更新。
？MySQL 中有更简单的方法： replace into

replace into t(id, update_time) values(1, now());
或
replace into t(id, update_time) select 1, now();
1
2
3
replace into 跟 insert 功能类似，不同点在于：replace into 首先尝试插入数据到表中， 1. 如果发现表中已经有此行数据（根据主键或者唯一索引判断）则先删除此行数据，然后插入新的数据。 2. 否则，直接插入新数据。
要注意的是：插入数据的表必须有主键或者是唯一索引！否则的话，replace into 会直接插入数据，这将导致表中出现重复的数据。
————————————————
mysql的replace into类似于oracle的merge sql语句_数据库_人生有酒多忘欢-CSDN博客.html
