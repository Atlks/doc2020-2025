Kill conn 批量杀死MySQL连接的四种方法详解

Demonson 2018-07-04 10:52:01  1594  收藏
分类专栏： MySQL 基础 MySQL 架构 MySQL 优化
这篇文章主要介绍了批量杀死MySQL连接的四种方法详解,本文分别给出了代码实例,需要的朋友可以参考下
方法一
　　通过information_schema.processlist表中的连接信息生成需要处理掉的MySQL连接的语句临时文件，然后执行临时文件中生成的指令。
复制代码 代码如下:

mysql> select concat('KILL ',id,';') from information_schema.processlist where user='root';
+------------------------+
| concat('KILL ',id,';') |
+------------------------+
| KILL 3101;             |
| KILL 2946;             |
+------------------------+
2 rows in set (0.00 sec)
 
mysql>select concat('KILL ',id,';') from information_schema.processlist where user='root' into outfile '/tmp/a.txt';
Query OK, 2 rows affected (0.00 sec)
 
mysql>source /tmp/a.txt;
Query OK, 0 rows affected (0.00 sec)

