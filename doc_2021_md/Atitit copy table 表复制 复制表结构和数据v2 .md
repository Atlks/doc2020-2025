Atitit copy table 表复制 复制表结构和数据

MySQL 复制表结构SHOW CREATE TABLE 
如果我们需要完全的复制MySQL的数据表，包括表的结构，索引，默认值等。 如果仅仅使用CREATE TABLE ... SELECT 命令，是无法实现的。
本章节将为大家介绍如何完整的复制MySQL数据表，步骤如下：
使用 SHOW CREATE TABLE 命令获取创建数据表(CREATE TABLE) 语句，该语句包含了原数据表的结构，索引等。

复制以下命令显示的SQL语句，修改数据表名，并执行SQL语句，通过以上命令 将完全的复制数据表结构。
如果你想复制表的内容，你就可以使用 INSERT INTO ... SELECT 语句来实现
5.6不能使用此语句

CREATE TABLE 新表 LIKE 旧表

3.1.17.3 CREATE TABLE ... LIKE語句  可以完整复制表结构
用於CREATE TABLE ... LIKE根據另一個表的定義創建一個空表，包括在原始表中定義的任何列屬性和索引：
CREATE TABLE new_tbl LIKE orig_tbl;
使用與原始表相同的表存儲格式版本創建副本。該 SELECT權限需要對原始表。
LIKE 僅適用於基表，不適用於視圖。

1.复制表结构及数据到新表CREATE TABLE
CREATE TABLE 新表 SELECT * FROM 旧表
2.只复制表结构到新表
CREATE TABLE 新表 SELECT * FROM 旧表 WHERE 1=2
即:让WHERE条件不成立.
方法二:(由tianshibao提供)
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

