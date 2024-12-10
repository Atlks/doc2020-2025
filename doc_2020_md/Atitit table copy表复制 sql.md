Atitit table copy表复制 sql  batch insert

select into与insert into区别

D_A_O 2016-06-07 10:43:43  2928  收藏 3
展开
select into from 和 insert into select都是用来复制表，两者的主要区别为： select into from 要求目标表不存在，因为在插入时会自动创建。insert into select from 要求目标表存在。
————————————————

sql语句复制一张表
1、复制表结构及数据到新表

CREATE TABLE 新表 SELECT * FROM 旧表
1
这种方法会将oldtable中所有的内容都拷贝过来，当然我们可以用delete from newtable;来删除。
不过这种方法的一个最不好的地方就是新表中没有了旧表的primary key、Extra（auto_increment）等属性。需要自己用”alter”添加，而且容易搞错。

2、只复制表结构到新表

CREATE TABLE 新表 SELECT * FROM 旧表 WHERE 1=2 或CREATE TABLE 新表 LIKE 旧表 
1
3、复制旧表的数据到新表(假设两个表结构一样)

INSERT INTO 新表 SELECT * FROM 旧表 
1
4、复制旧表的数据到新表(假设两个表结构不一样)

INSERT INTO 新表(字段1,字段2,.......) SELECT 字段1,字段2,...... FROM 旧表 
1
5、这样会将旧表的创建命令列出。我们只需要将该命令拷贝出来，更改table的名字，就可以建立一个完全一样的表

show create table 旧表; 
————————————————
MySQL 复制表
如果我们需要完全的复制MySQL的数据表，包括表的结构，索引，默认值等。 如果仅仅使用CREATE TABLE ... SELECT 命令，是无法实现的。
本章节将为大家介绍如何完整的复制MySQL数据表，步骤如下：
使用 SHOW CREATE TABLE 命令获取创建数据表(CREATE TABLE) 语句，该语句包含了原数据表的结构，索引等。

复制以下命令显示的SQL语句，修改数据表名，并执行SQL语句，通过以上命令 将完全的复制数据表结构。
如果你想复制表的内容，你就可以使用 INSERT INTO ... SELECT 语句来实现。
来给大家区分下mysql复制表的两种方式。
第一、只复制表结构到新表
create table 新表 select * from 旧表 where 1=2
或者
create table 新表 like 旧表 
第二、复制表结构及数据到新表
create table新表 select * from 旧

