Atitit mysql 重要参数top10



加快速度类
调整隔离级别为读已提交
set global transaction isolation level read committed;    
show global variables like '%tx_isolation%';


Cache类

innodb_buffer_pool_size ..数据体积+20%冗余。。（最重要参数）
过大会导致多余对swap os cache磁盘占用


innodb_buffer_pool_size：缓存数据块和索引块，对InnoDB表性能影响最大。通过查询show status like 'Innodb_buffer_pool_read%'，保证 (Innodb_buffer_pool_read_requests – Innodb_buffer_pool_reads) / Innodb_buffer_pool_read_requests越高越好


将事务日志刷盘模式调整为定时刷新（重要）
set global  innodb_flush_log_at_trx_commit=2;

默认是每次事务就刷新，调整为每秒刷新

提升性能越约8倍



事务日志文件体积调整
Mysql5.6 只能在配置文件中修改此配置，调整为500M， 影响写入速度，以及重启速度
 innodb_log_file_size=500123456
设置的太小：当一个日志文件写满后，innodb会自动切换到另外一个日志文件，而且会触发数据库的检查点（Checkpoint），这会导致innodb缓存脏页的小批量刷新，会明显降低innodb的性能。
设置的太大：设置很大以后减少了checkpoint，并且由于redo log是顺序I/O，大大提高了I/O性能。但是如果数据库意外出现了问题，比如意外宕机，那么需要重放日志并且恢复已经提交的事务，如果日志很大，那么将会导致恢复时间很长。
会影响启动速度，可以测试，普通机器300M可以了。。
调整事务日志cache体积  innodb_log_buffer_size
Mysql5.6 只能在配置文件中修改此配置，默认8M，调大10倍
 innodb_log_buffer_size=80123456

多线程类的参数
适当增大读写写线程数目 innodb_write_io_threads
只能在配置文件里面调整，调整为cpu核心数
innodb_read_io_threads = 32
innodb_write_io_threads = 32


假如CPU是2颗8核的，那么可以设置：
innodb_read_io_threads = 8
innodb_write_io_threads = 8

增大连接数（已调整，影响并发）
innodb_thread_concurrency线程数量（保持默认0自动配置）



