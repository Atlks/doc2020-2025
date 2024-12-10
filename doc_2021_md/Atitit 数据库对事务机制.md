Atitit 数据库对事务机制


1.事务提交的方式
在MariaDB/MySQL中有3种事务提交的方式。
1.显式开启和提交。
使用begin或者start transaction来显式开启一个事务，显式开启的事务必须使用commit或者rollback显式提交或回滚。几种特殊的情况除外：行版本隔离级别下的更新冲突和死锁会自动回滚。
在存储过程中开启事务时必须使用start transaction，因为begin会被存储过程解析为begin...end结构块。
另外，MariaDB/MySQL中的DDL语句会自动提交前面所有的事务（包括显示开启的事务），而在SQL Server中DDL语句还是需要显式提交的，也就是说在SQL Server中DDL语句也是可以回滚的。
2.自动提交。(MySQL默认的提交方式)
不需要显式begin或者start transaction来显式开启事务，也不需要显式提交或回滚事务，每次执行DML和DDL语句都会在执行语句前自动开启一个事务，执行语句结束后自动提交或回滚事务。
3.隐式提交事务
隐式提交事务是指执行某些语句会自动提交事务，包括已经显式开启的事务。
会隐式提交事务的语句主要有：
(1).DDL语句(其中有truncate table)。
(2).隐式修改mysql数据库架构的操作:create user,drop user,grant,rename user,revoke,set password。
(3).管理语句：analyze table、cache index、check table、load index into cache、optimize table、repair table。
通过设置 auto_commit 变量值为1或0来设置是否自动提交，为1表示自动提交，0表示关闭自动提交，即必须显式提交。但是不管设置为0还是1，显式开启的事务必须显式提交，而且隐式提交的事务不受任何人为控制。

