Atitit mysql insert perf enhance


方案三：ON DUPLICATE KEY UPDATE
如‍上所写，你也可以在INSERT INTO…..后面加上 ON DUPLICATE KEY UPDATE方法来实现。如果您指定了ON DUPLICATE KEY UPDATE，并且插入行后会导致在一个UNIQUE索引或PRIMARY KEY中出现重复值，则执行旧行UPDATE。
您可以在UPDATE子句中使用VALUES(col_name)函数从INSERT…UPDATE语句的INSERT部分引用列值。换句话说，如果没有发生重复关键字冲突，则UPDATE子句中的VALUES(col_name)可以引用被插入的col_name的值。本函数特别适用于多行插入。VALUES()函数只在INSERT…UPDATE语句中有意义，其它时候会返回NULL。
INSERT INTO `table` (`a`, `b`, `c`) VALUES (1, 2, 3), (4, 5, 6) 
ON DUPLICATE KEY UPDATE `c`=VALUES(`a`)+VALUES(`b`);
本语句与以下两个语句作用相同：
INSERT INTO `table` (`a`, `b`, `c`) VALUES (1, 2, 3) ON DUPLICATE KEY UPDATE `c`=3; 
INSERT INTO `table` (`a`, `b`, `c`) VALUES (4, 5, 6) ON DUPLICATE KEY UPDATE c=9;


案一：使用ignore关键字


如果是用主键primary或者唯一索引unique区分了记录的唯一性,避免重复插入记录可以使用：
INSERT IGNORE INTO `table_name` (`email`, `phone`, `user_id`) 
VALUES ('test9@163.com', '99999', '9999');
 
这样当有重复记录就会忽略,执行后返回数字0

其它关键：DELAYED  做为快速插入，并不是很关心失效性，提高插入性能。
IGNORE  只关注主键对应记录是不存在，无则添加，有则忽略。

MySQL 5.6参考手册  /  ...  /  INSERT DELAYED语句
13.2.5.3 INSERT DELAYED语句  异步
INSERT DELAYED ...
该语句的DELAYED选项 INSERT是对标准SQL的MySQL扩展，可用于某些类型的表（例如MyISAM）。当客户端使用时 INSERT DELAYED，它将立即从服务器获得许可，并且当该表未被任何其他线程使用时，该行将排队插入。
注意
INSERT DELAYEDINSERT如果不使用该表，则它比正常速度慢。服务器还要为每个有延迟行的表处理一个单独的线程，这会产生额外的开销。这意味着INSERT DELAYED仅在确实确定需要时才应使用 。
从MySQL 5.6.6开始，INSERT DELAYED已弃用，并将在以后的版本中删除。使用INSERT （不带DELAYED）代替。
排队的行仅保留在内存中，直到将它们插入表中为止。这意味着，如果强行终止mysqld（例如，使用 kill -9）或mysqld意外终止 ，则所有尚未写入磁盘的排队行都将丢失。
使用以下限制 DELAYED：

INSERT DELAYED只有工作MyISAM，MEMORY， ARCHIVE，和BLACKHOLE 表格。对于不支持的引擎， DELAYED会发生错误。


INSERT DELAYED如果将其与已锁定的表一起使用， 则会发生错误，LOCK TABLES因为插入必须由单独的线程而不是由持有锁的会话处理。


对于MyISAM表，如果数据文件中间没有空闲块，则支持并发 SELECT和 INSERT语句。在这种情况下，你很少需要使用INSERT DELAYED带 MyISAM。


INSERT DELAYED仅应用于INSERT指定值列表的语句。服务器忽略 DELAYEDfor INSERT ... SELECT或 INSERT ... ON DUPLICATE KEY UPDATE语句。


因为该INSERT DELAYED 语句立即返回，所以在插入行之前，您不能使用它 LAST_INSERT_ID()来获取AUTO_INCREMENT该语句可能生成的 值。


DELAYED在SELECT实际插入之前，行对语句不可见 。


INSERT DELAYED每当is 或的值时，将作为简单的INSERT（即不带DELAYED选项）进行处理。（在后一种情况下，该语句不会触发切换到基于行的日志记录，因此将使用基于语句的格式进行记录。） binlog_formatSTATEMENTMIXED

当使用基于行的二进制日志记录模式（binlog_format设置为 ROW）时，该方法不适用，在该模式下， INSERT DELAYED始终使用DELAYED指定的选项执行语句并将其记录为行更新事件。


DELAYED在从属复制服务器上被忽略，因此在从属服务器上INSERT DELAYED被视为正常 INSERT。这是因为DELAYED可能导致从机拥有与主机不同的数据。


INSERT DELAYED 如果表被写锁定并ALTER TABLE用于修改表结构，则 待处理语句将丢失 。


INSERT DELAYED 视图不支持。


INSERT DELAYED 不支持分区表。

以下详细描述了使用DELAYED选项 INSERT或 时会发生什么 REPLACE。在本说明中， “ 线程 ”是接收INSERT DELAYED语句 的线程， “ 处理程序 ”是处理INSERT DELAYED特定表的所有语句的线程 。

当线程执行DELAYED 表的DELAYED语句时，如果尚不存在处理程序线程，则会创建一个处理程序线程来处理该表的所有语句。


线程检查处理程序以前是否已获取DELAYED锁；如果不是，它告诉处理程序线程这样做。DELAYED 即使其他线程在表上具有READ或WRITE锁，也可以获得该锁 。但是，处理程序将等待所有 ALTER TABLE锁或 FLUSH TABLES语句完成，以确保表结构是最新的。


该线程执行该 INSERT语句，但不是将行写入表中，而是将最后一行的副本放入由处理程序线程管理的队列中。该线程会发现任何语法错误，并将其报告给客户端程序。


客户端无法从服务器获取重复的行数或AUTO_INCREMENT 结果行的值，因为 INSERT插入操作完成之前的返回。（如果使用C API，则mysql_info()由于相同的原因，该函数不会返回任何有意义的信息。）


当将行插入表中时，处理程序线程会更新二进制日志。如果是多行插入，则在插入第一行时更新二进制日志。


每次 delayed_insert_limit写入行时，处理程序都会检查是否还有任何 SELECT语句尚未处理。如果是这样，则允许它们在继续之前执行。


当处理程序的队列中没有更多行时，该表将被解锁。如果INSERT DELAYED在delayed_insert_timeout 几秒钟内未收到新语句 ，则处理程序终止。


如果delayed_queue_size在特定处理程序队列中有多个 行挂起，则请求线程 INSERT DELAYED等待，直到队列中有空间为止。这样做是为了确保 mysqld不会将所有内存用于延迟的内存队列。


处理程序线程显示在MySQL进程列表 delayed_insert中的 Command列中。如果执行一条FLUSH TABLES 语句或使用杀死它，它将被杀死。但是，在退出之前，它首先将所有排队的行存储到表中。在此期间，它不接受来自其他线程的任何新 语句。如果在此之后执行语句，则会创建一个新的处理程序线程。 KILL thread_idINSERTINSERT DELAYED

这意味着，如果有 处理程序正在运行，则INSERT DELAYED语句的优先级高于普通INSERT语句INSERT DELAYED。其他更新语句必须等到INSERT DELAYED队列为空，有人终止处理程序线程（带有 ）或有人执行。 KILL thread_idFLUSH TABLES


以下状态变量提供有关INSERT DELAYED语句的信息 。


您可以通过发出SHOW STATUS语句或执行mysqladmin extended-status 命令来查看这些变量 。

Archil引擎
Mem引擎
去除插入触发器，改为update触发器模式  手动刷新 
在没有更新update之前，加个fullfld标识。。可以不在select显示，只有update过了，才在ui显示

插入触发器改用代码实现 一次更新一条
严禁批量更新默认是一个长事务 可用代码拆分细分
检查移除多进程，防止多个进程同时更改同一记录
