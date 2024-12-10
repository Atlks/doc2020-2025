Atitit copy table 表复制 复制表结构和数据


1.复制表结构及数据到新表CREATE TABLE
CREATE TABLE 新表 SELECT * FROM 旧表
2.只复制表结构到新表
CREATE TABLE 新表 SELECT * FROM 旧表 WHERE 1=2
即:让WHERE条件不成立.
方法二:(由tianshibao提供)
CREATE TABLE 新表 LIKE 旧表
INSERT INTO SELECT

3.复制旧表的数据到新表(假设两个表结构一样)
INSERT INTO 新表 SELECT * FROM 旧表
4.复制旧表的数据到新表(假设两个表结构不一样)
INSERT INTO 新表(字段1,字段2,.......) SELECT 字段1,字段2,...... FROM 旧表
SELECT INTO 和 INSERT INTO SELECT 两种表复制语句的区别
使用 SQL 进行数据复制的时候，会有 SELECT INTO 和 INSERT INTO SELECT 两种语句用法，下面简单罗列一下大概的区别：
1.INSERT INTO SELECT 语句：
INSERT INTO Table2(field1,field2,...) SELECT value1,value2,... FROM Table1
要求目标表Table2必须存在，由于目标表Table2已经存在，所以我们除了插入源表Table1的字段外，还可以插入常量。
2.SELECT INTO FROM语句
INSERT INTO SELECT vale1, value2 into Table2 from Table1
要求目标表Table2不存在，因为在插入时会自动创建表Table2，并将Table1中指定字段数据复制到Table2中。

