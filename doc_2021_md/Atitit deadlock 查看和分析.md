Atitit deadlock 查看和分析












show OPEN TABLES where In_use > 0;

select * from information_schema.innodb_trx

Locks
和lockswait表

死锁日志

Deaklockcheck  5.7以后有此参数


3、在5.5中，information_schema 库中增加了三个关于锁的表（innoDB引擎）：

innodb_trx         ## 当前运行的所有事务
innodb_locks       ## 当前出现的锁
innodb_lock_waits  ## 锁等待的对应关系
