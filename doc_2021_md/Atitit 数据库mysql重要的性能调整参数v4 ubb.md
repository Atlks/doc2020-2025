Atitit 数据库mysql重要的性能调整参数



主要优化对方面
优化死锁  sql优化
缩短响应时间   cache
多线程优化
优化死锁方面的
死锁检测 开启 与死锁超时配置
配置锁定类对参数，调小锁等待间隔

尽可能小对事务范围
Sp服务化 固定的顺序访问表

降低隔离级别为rc，防止gap锁死锁 
比如将隔离级别从RR调整为RC，可以避免掉很多因为gap锁造成的死锁。
更改隔离级别到读已提交（oracle mssql pgsql等大多数数据库的默认隔离级别）

Mysql隔离级别太高了，会造成性能问题。。很多项目也是建议更改此隔离级别read commited
业务正确性不必担心，oracle也是用此隔离级别read commited。。

经过测试，可以解决行锁变表锁的问题。。。

在业务环境允许的情况下，尽量使用较低级别的事务隔离，以减少MySQL 因为实现事务隔离级
别所带来的附加成本；

为表添加合理的索引。防止没有索引出现表锁，出现的死锁的概率会突增。
更新mysql版本。
8比5.7提升2倍性能，5.7比5.6提升约也有三倍

数据结算独立性可能需要加强，每个结果不应该影响另外一条
每个用户数据不影响另外用户，，每个订单数据不会影响另外一个

缩短执行时间，提升响应速度
适当分库分区 缩小锁定范围
调整 lock_wait_timeout 设置更改结构时对超时（重要）

某条记录有行锁，则不能增加字段等操作。。需要设置超时


避免长时间占用锁 wait_timeout 事务超时时间 （重要）
更改这个后。。事务超时会自动结束。。查询所在的事务使用此语句查询。。
SELECT * FROM information_schema.INNODB_TRX
应用中的一个事务性方法锁住了一条记录(select … for update), 并在锁住记录后陷入了死循环，由此导致其它事务对该条记录的任何操作都会处于等待中。此问题也可以理解为，一个事务加锁了某些记录，但是长时间不提交，导致大量事务等待超时。那这个超时时间是多少呢？如何控制这个超时时间呢？
wait_timeout
wait_timeout是mysql的一个系统变量，可以通过启动时的命令行参数--wait-timeout来指定，也可以在运行时动态指定，支持session和Global。


各种timeout的设置 缩短

 show global variables like '%timeout%'
set global lock_wait_timeout = 20; --

| Variable_name                | Value    |
+------------------------------+----------+
| connect_timeout              | 10       |
| delayed_insert_timeout       | 300      |
| innodb_flush_log_at_timeout  | 1        |
| innodb_lock_wait_timeout     | 120      |
| innodb_rollback_on_timeout   | ON       |
| interactive_timeout          | 172800   |
| lock_wait_timeout            | 31536000 |
| net_read_timeout             | 30       |
| net_write_timeout            | 60       |
| rpl_semi_sync_master_timeout | 10000    |
| rpl_stop_slave_timeout       | 31536000 |
| slave_net_timeout            | 10       |
| wait_timeout                 | 172800  


RDS MySQL各timeout参数的设置
 show global variables like '%timeout%'
set global lock_wait_timeout = 20; --
set global  deadlock_timeout_long=10;
set global  deadlock_timeout_short=10;

RDS MySQL提供了很多的timeout参数供用户设置，本文详细介绍下这些timeout参数的含义。


参见
MySQL 各种超时参数的含义 - xiaoboluo768 - 博客园

Mysql 重要top5 性能参数

 innodb_buffer_pool_size 大概为70%内存
 show global variables like '%buffer%';
 show global variables like '%innodb_flush_log_at_trx_commit%';
set global  innodb_buffer_pool_size=1241000111;
-- readonly   set global  innodb_log_buffer_size=80333666;
set global  innodb_flush_log_at_trx_commit=2;

2. 保证从内存中读取数据，讲数据保存在内存中
2.1 足够大的 innodb_buffer_pool_size
推荐将数据完全保存在 innodb_buffer_pool_size ，即按存储量规划 innodb_buffer_pool_size 的容量。这样你可以完全从内存中读取数据，最大限度减少磁盘操作。

2.1.1 如何确定 innodb_buffer_pool_size 足够大，数据是从内存读取而不是硬盘？
方法 1

mysql> SHOW GLOBAL STATUS LIKE 'innodb_buffer_pool_pages_%';
+----------------------------------+--------+| Variable_name                    | Value  |
+----------------------------------+--------+
| Innodb_buffer_pool_pages_data    | 129037 || Innodb_buffer_pool_pages_dirty   | 362    |
| Innodb_buffer_pool_pages_flushed | 9998   || Innodb_buffer_pool_pages_free    | 0      |  !!!!!!!!
| Innodb_buffer_pool_pages_misc    | 2035   || Innodb_buffer_pool_pages_total   | 131072 |
+----------------------------------+--------+
6 rows in set (0.00 sec)
发现 Innodb_buffer_pool_pages_free 为 0，则说明 buffer pool 已经被用光，需要增大 innodb_buffer_pool_size

InnoDB 的其他几个参数：

innodb_additional_mem_pool_size = 1/200 of buffer_pool
innodb_max_dirty_pages_pct 80%
innodb_flush_log_at_trx_commit=2
transaction_isolation =READ-COMMITTED
 READ-UNCOMMITTED | READ-COMMITTED

innodb_log_buffer_size=80333666
5.6默认8M

set global  innodb_buffer_pool_size=1241000111;
-- readonly   set global  innodb_log_buffer_size=80333666

innodb_log_file_size 为25% innodb_buffer_pool_size

 一般太小的logfile size的表现情况就是checkpoint比较频繁，导致刷新dirty page到磁盘的次数增加，在
刷新时会使整个系统变得很慢.所以这种情况要尽量避免.
  从例子中得知当前的innodb_log_file_sze为5M 是远远不够的.

4.1 使用足够大的写入缓存 innodb_log_file_size
但是需要注意如果用 1G 的 innodb_log_file_size ，假如服务器当机，需要 10 分钟来恢复。
推荐 innodb_log_file_size 设置为 0.25 * innodb_buffer_pool_size

other
 innodb_flush_method=O_DIRECT   cant use in mysql5.6


－影响InnoDB性能的一些重要参数－－－－－－－－－－－－－－

1）InnoDB_buffer_pool_size
这个参数定义InnoDB存储引擎的表数据和索引数据的最大内存缓冲区,InnoDB_buffer_pool_size参数同时提供为数据块和索引块做缓存.这个值设置的越高,访问表中数据需要的磁盘IO就越少.
2）InnoDB_flush_log_at_trx_commit
这个参数控制缓冲区的数据写入到日志文件以及日志文件数据刷新到磁盘的操作时机.在正式环境中建议设置成1。
设置0时日志缓冲每秒一次被写到日志文件,并且对日志文件做向磁盘刷新的操作,但是在一个事物提交不做任何操作.
设置1时在每个事物提交时,日志缓冲被写到日志文件,并且对日志文件做向磁盘刷新的操作
设置2时在每个事物提交时,日志缓冲被写到日志文件,但不对日志文件做向磁盘刷新的操作,对日志文件每秒向磁盘做一次刷新操作.
3）InnoDB_additional_mem_pool_size 表很多对时候需要
这个参数是InnoDB用来存储数据库结构和其他内部数据结构的内存池.应用程序的表越多,则需要从这里分配越多的内存,如果用光这个池,则会从OS层分配.
  6）InnoDB_log_buffer_size
这个参数日志缓冲大小
7）InnoDB_log_file_size
这个参数是一个日志组中每个日志文件的大小,此参数在高写入负载尤其是大数据集的情况下很重要.这个值越大则性能相对越高,但好似副作用是一旦系统崩溃恢复的时间会加长.
8）Innodb_io_capacity
这个参数刷新脏页数量和合并插入数量，改善磁盘IO处理能力
9）Innodb_use_native_aio
异步I/O在一定程度上提高系统的并发能力，在Linux系统上，可以通过将MySQL的服务器此参数的值设定为ON设定InnoDB可以使用Linux的异步I/O子系统.
10）Innodb_read_io_threads
这个参数可调整的读请求的后台线程数
11）Innodb_write_io_threads
这个参数可调整的写请求的后台线程数
12）InnoDB_buffer_pool_instances
这个参数能较好的运行于多核处理器，支持使用 此参数对服务器变量建立多个缓冲池实例，每个缓冲池实例分别自我管理空闲列表、列表刷写、LRU以及其它跟缓冲池相关的数据结构，并通过各自的互斥锁进行保护
13）InnoDB_purge_threads
MySQL5.5以前碎片回收操作是主线程的一部分，这经定期调度的方式运行，但会阻塞数据库的其他操作.到5.5以后，可以将这个线程独立出来 ；这个能让碎片回收得更及时而且不影响其他线程的操作
14）Innodb_flush_method
这个参数控制着innodb数据文件及redo log的打开、刷写模式，对于这个参数，文档上是这样描述的：
有三个值：fdatasync(默认)，O_DSYNC，O_DIRECT
默认是fdatasync，调用fsync()去刷数据文件与redo log的buffer
为O_DSYNC时，innodb会使用O_SYNC方式打开和刷写redo log,使用fsync()刷写数据文件
为O_DIRECT时，innodb使用O_DIRECT打开数据文件，使用fsync()刷写数据文件跟redo log
总结一下三者写数据方式：
fdatasync模式：写数据时，write这一步并不需要真正写到磁盘才算完成（可能写入到操作系统buffer中就会返回完成），真正完成是flush操作，buffer交给操作系统去flush,并且文件的元数据信息也都需要更新到磁盘。
O_DSYNC模式：写日志操作是在write这步完成，而数据文件的写入是在flush这步通过fsync完成
O_DIRECT模式：数据文件的写入操作是直接从mysql innodb buffer到磁盘的，并不用通过操作系统的缓冲，而真正的完成也是在flush这步,日志还是要经过OS缓冲

提升响应速度 缩短语句时间
日志定时刷新 vs 即时刷新innodb_flush_log_at_trx_commit

innodb_flush_log_at_trx_commit
更新数据库版本
更近的距离 数据库端代码sp
更近的距离  同机部署
缩短锁定时间  让我们的修改类 Query 执行时间尽可能的短
唯一的办法就是让我们的Query 执行时间尽可能的短。
a) 尽两减少大的复杂Query，将复杂Query 分拆成几个小的Query 分布进行；
b) 尽可能的建立足够高效的索引，让数据检索更迅速；
更改隔离级别到读已提交（oracle mssql pgsql等大多数数据库的默认隔离级别）

Mysql隔离级别太高了，会造成性能问题。。很多项目也是建议更改此隔离级别read commited
业务正确性不必担心，oracle也是用此隔离级别read commited。。

经过测试，可以解决行锁变表锁的问题。。。

在业务环境允许的情况下，尽量使用较低级别的事务隔离，以减少MySQL 因为实现事务隔离级
别所带来的附加成本；


升级到mysql8  性能优化了很多
功能改进：
JSON支持包含许多新增功能，包括接受JSON数据并将其作为关系表返回的JSON_TABLE()函数。
速度提高2倍(对比MySQL5.7)，并创建新的基准测试记录，每秒最多180万个查询，MySQL 8.0比MySQL 5.7快2倍，并设置了新的基准测试记录。
MySQL 5.7 主要增强了性能、可扩展性与管理能力。 在 SysBench试中，基于 1204 个链接的 Read-only Point-Selects 每秒传递 160 万次查询（QPS），为 MySQL 5.6 的 3 倍。

单独实例
多条sql处理下缩短网络io（重要）
网络io延时会带来事务延时，造成锁定时间和响应过长。。可以改变部署方式，将重要业务功能部署到和数据库服务器同一台物理机器上。。免去网络交互对时间

优先同机器部署，其次内网部署。。

如果云服务器，貌似只能使用sp存储过程模式将部分代码迁移到数据库内了。。
Sql优化  索引优化 
更新cache 与索引延迟机制
innodb_flush_method=O_DIRECT  避免双缓存 提升响应速度
分区机制
NoSQL功能 支持json  kv存储
适当使用数据库的拦截器机制事件机制 trigger触发器
适当使用外键等约束检查，减少网络往返io性能消耗
Unique索引等约束的使用
设置db多线程
innodb_thread_concurrency线程数量

同时在Innodb内核中处理的线程数量。建议默认值。
设置方法，在my.cnf文件里：
innodb_thread_concurrency = 16

适当增大写入线程数目 innodb_write_io_threads
假如CPU是2颗8核的，那么可以设置：
innodb_read_io_threads = 8
innodb_write_io_threads = 8
如果数据库的读操作比写操作多，那么可以设置：
innodb_read_io_threads = 10
innodb_write_io_threads = 6
在MySQL5.1.X版本中，innodb_file_io_threads参数默认是4，该参数在Linux系统上是不可更改的，但Windows系统上可以调整。这个参数的作用是：InnoDB使用后台线程处理数据页上读写I/O（输入输出）请求的数量。
在MySQL5.5.X版本中，或者说是在InnoDB Plugin1.0.4以后，就用两个新的参数，即innodb_read_io_threads和innodb_write_io_threads，取代了innodb_file_io_threads如此调整后，在Linux平台上就可以根据CPU核数来更改相应的参数值了，默认是4。
innodb_read_io_threads 
Dep  innodb_file_io_threads文件读写IO数
在MySQL5.5.X版本中，或者说是在InnoDB Plugin1.0.4以后，就用两个新的参数，即innodb_read_io_threads和innodb_write_io_threads，取代了innodb_file_io_threads如此调整后，
 适当调大数据库连接数

调整数据库连接池参数
other
innodb_thread_concurrency设置InnoDB可以保持打开状态的并发线程数的上限。通常建议为此设置为（2 X CPU数量）+磁盘数量。去年，我从Percona NYC大会上第一手了解到，您应该将其设置为0，以提醒InnoDB Storage Engine为正在运行的环境找到最佳线程数。
innodb_concurrency_tickets设置可以绕过并发检查而不受惩罚的线程数。达到该限制之后，线程并发检查再次成为常态。
innodb_commit_concurrency设置可以提交的并发事务数。由于默认值为0，因此未设置此选项将允许任意数量的事务同时提交。
innodb_thread_sleep_delay设置在重新输入InnoDB队列之前InnoDB线程可以处于休眠状态的毫秒数。默认值为10000（10秒）。
innodb_read_io_threads（将其设置为3000）和innodb_write_io_threads（将其设置为7000）（均从MySQL 5.1.38开始）为读取和写入分配指定数量的线程。默认值为4，最大值为64。将其设置为64。此外，将innodb_io_capacity设置为10000。

-----------各种cache类参数调整
Insert delayed  update delete 延迟


由於InnoDB不支持INSERT DELAYED，因此使用大型InnoDB緩衝池是最接近INSERT DELAYED的方法。所有DML（INSERT，UPDATE和DELETE）都將被緩存在InnoDB緩衝池中。寫入的事務性信息將立即寫入重做日誌（ib_logfile0，ib_logfile1）。定期通過ibdata1（二級索引的InsertBuffer，雙寫入緩衝區）將內存中張貼的寫入緩衝區中的內容從內存刷新到磁盤。緩衝池越大，可以緩存的INSERT數量就越大。在具有8GB或更多RAM的系統中，將75-80％的RAM用作innodb_buffer_pool_size。在RAM很少的系統中，為25％（以容納OS）。
设置更高的innodb_buffer_pool_size 重要

InnoDB是一个非常不错的引擎。但是，它高度依赖于“调整”。 可以通过设置更高的innodb_buffer_pool_size来轻松克服。我的建议是将其设置为总RAM的60-70％。我现在正在生产中运行4台这样的服务器，每分钟插入约350万行。他们已经有将近3 TB的数据。InnoDB由于必须高度并发插入，因此必须为InnoDB。还有其他加快插入的方法。我已经对一些基准进行了基准测试。

show global status like '%Innodb_buffer_pool%';

 innodb_buffer_pool_size默认大小为128M

缓冲池（由innodb_buffer_pool_size调整大小）
由于InnoDB不支持INSERT DELAYED，因此使用大型InnoDB缓冲池是最接近INSERT DELAYED的方法。所有DML（INSERT，UPDATE和DELETE）都将被缓存在InnoDB缓冲池中。Writes的事务性信息将立即写入重做日志（ib_logfile0，ib_logfile1）。通过ibdata1（二级索引的InsertBuffer，双写缓冲区）定期将缓冲区池中发布的写入从内存刷新到磁盘。缓冲池越大，可以缓存的INSERT数量就越大。在具有8GB或更多RAM的系统中，将75-80％的RAM用作innodb_buffer_pool_size。在RAM很少的系统中，为25％（以容纳OS）。
CAVEAT：您可以将innodb_doublewrite设置为0来加快写入速度，但是有数据完整性的风险。您还可以通过将innodb_flush_method设置为O_DIRECT来加快处理速度，以防止将InnoDB缓存到操作系统。
重做日志（大小为innodb_log_file_size）
缺省情况下，重做日志名为ib_logfile0和ib_logfile1，每个重做日志为5MB。该大小应为innodb_buffer_pool_size的25％。如果重做日志已经存在，则在my.cnf中添加新设置，关闭mysql，删除它们，然后重新启动mysql。
日志缓冲区（由innodb_log_buffer_size调整大小）
日志缓冲区将更改保存到RAM中，然后再将其刷新到重做日志中。默认值为8M。日志缓冲区越大，磁盘I / O越少。


物化视图机制（mysql需要使用timer机制实现刷新）
Timer事件机制也可以适当使用  提升性能 延后异步处理一些事物
12. 配置全面使用db数据库的cache机制	21
12.1. 全面调整mysql的cache类参数	21
12.2. 适当开启query cache	21
12.3. innodb_flush_method=O_DIRECT  避免双缓存 提升响应速度	21
12.4. 启用修改延迟法 cache法 提升insert类的性能 Insert delay	22
12.5. Cache 事务日志配置	22
12.6. 是否有延迟索引机制	22
12.7. 使用内存表存储引擎 做更新cache	23
12.8. 适当使用临时表机制	23
12.9. 适当使用分区机制	23
优化事务日志方面的

2）关于日志方面：
innodb_log_file_size
作用：指定在一个日志组中，每个log的大小。
结合innodb_buffer_pool_size设置其大小，25%-100%。避免不需要的刷新。
注意：这个值分配的大小和数据库的写入速度，事务大小，异常重启后的恢复有很大的关系。一般取256M可以兼顾性能和recovery的速度。
分配原则：几个日值成员大小加起来差不多和你的innodb_buffer_pool_size相等。上限为每个日值上限大小为4G.一般控制在几个Log文件相加大小在2G以内为佳。具体情况还需要看你的事务大小，数据大小为依据。
说明：这个值分配的大小和数据库的写入速度，事务大小，异常重启后的恢复有很大的关系。
设置方法：在my.cnf文件里：
innodb_log_file_size = 256M
innodb_log_files_in_group
作用：指定你有几个日值组。
分配原则：　一般我们可以用2-3个日值组。默认为两个。
设置方法：在my.cnf文件里：
innodb_log_files_in_group=3
innodb_log_buffer_size：日志缓冲区

作用：事务在内存中的缓冲，也就是日志缓冲区的大小， 默认设置即可，具有大量事务的可以考虑设置为16M。
如果这个值增长过快，可以适当的增加innodb_log_buffer_size
另外如果你需要处理大理的TEXT，或是BLOB字段，可以考虑增加这个参数的值。
设置方法：在my.cnf文件里：
innodb_log_buffer_size=3M
innodb_flush_logs_at_trx_commit  控制事务的log的刷新方式 重要调整

作用：控制事务的提交方式,也就是控制log的刷新到磁盘的方式。
分配原则：这个参数只有3个值（0，1，2）.默认为1，性能更高的可以设置为0或是2，这样可以适当的减少磁盘IO（但会丢失一秒钟的事务。），游戏库的MySQL建议设置为0。主库请不要更改了。
其中：
0：log buffer中的数据将以每秒一次的频率写入到log file中，且同时会进行文件系统到磁盘的同步操作，但是每个事务的commit并不会触发任何log buffer 到log file的刷新或者文件系统到磁盘的刷新操作；
1：（默认为1）在每次事务提交的时候将logbuffer 中的数据都会写入到log file，同时也会触发文件系统到磁盘的同步；
2：事务提交会触发log buffer 到log file的刷新，但并不会触发磁盘文件系统到磁盘的同步。此外，每秒会有一次文件系统到磁盘同步操作。
说明：
这个参数的设置对Ｉｎｎｏｄｂ的性能有很大的影响，所以在这里给多说明一下。
当这个值为1时：innodb 的事务LOG在每次提交后写入日值文件，并对日值做刷新到磁盘。这个可以做到不丢任何一个事务。
当这个值为2时：在每个提交，日志缓冲被写到文件，但不对日志文件做到磁盘操作的刷新,在对日志文件的刷新在值为2的情况也每秒发生一次。但需要注意的是，由于进程调用方面的问题，并不能保证每秒１００％的发生。从而在性能上是最快的。但操作系统崩溃或掉电才会删除最后一秒的事务。
当这个值为0时：日志缓冲每秒一次地被写到日志文件，并且对日志文件做到磁盘操作的刷新，但是在一个事务提交不做任何操作。mysqld进程的崩溃会删除崩溃前最后一秒的事务。
从以上分析，当这个值不为１时，可以取得较好的性能，但遇到异常会有损失，所以需要根据自已的情况去衡量。
设置方法：在my.cnf文件里：
innodb_flush_logs_at_trx_commit=1
3）文件IO分配，空间占用方面
innodb_file_per_table  每个Innodb的表，有自已独立的表空间

作用：使每个Innodb的表，有自已独立的表空间。如删除文件后可以回收那部分空间。默认是关闭的，建议打开（innodb_file_per_table=1）
分配原则：只有使用不使用。但DB还需要有一个公共的表空间。
设置方法：在my.cnf文件里：
innodb_file_per_table=1
innodb_file_io_threads文件读写IO数

作用：文件读写IO数，这个参数只在Windows上起作用。在Linux上只会等于4，默认即可！
设置方法：在my.cnf文件里：
innodb_file_io_threads=4
innodb_open_files
作用：限制Innodb能打开的表的数据。
分配原则：这个值默认是300。如果库里的表特别多的情况，可以适当增大为1000。innodb_open_files的大小对InnoDB效率的影响比较小。但是在InnoDBcrash的情况下，innodb_open_files设置过小会影响recovery的效率。所以用InnoDB的时候还是把innodb_open_files放大一些比较合适。
设置方法：在my.cnf文件里：
innodb_open_files=800
innodb_data_file_path
指定表数据和索引存储的空间，可以是一个或者多个文件。最后一个数据文件必须是自动扩充的，也只有最后一个文件允许自动扩充。这样，当空间用完后，自动扩充数据文件就会自动增长（以8MB为单位）以容纳额外的数据。
例如： innodb_data_file_path=/disk1/ibdata1:900M;/disk2/ibdata2:50M:autoextend 两个数据文件放在不同的磁盘上。数据首先放在ibdata1 中，当达到900M以后，数据就放在ibdata2中。
设置方法，在my.cnf文件里：
innodb_data_file_path =ibdata1:1G;ibdata2:1G;ibdata3:1G;ibdata4:1G;ibdata5:1G;ibdata6:1G:autoextend
innodb_data_home_dir
放置表空间数据的目录，默认在mysql的数据目录，设置到和MySQL安装文件不同的分区可以提高性能。
设置方法，在my.cnf文件里：（比如mysql的数据目录是/data/mysql/data，这里可以设置到不通的分区/home/mysql下）
innodb_data_home_dir = /home/mysql
4）其它相关参数（适当的增加table_cache）

这里说明一个比较重要的参数：

Innodb_io_capacity 增大十倍

这个参数刷新脏页数量和合并插入数量，改善磁盘IO处理能力


Cant use innodb_flush_method O_DIRECT


作用：Innodb和系统打交道的一个IO模型
分配原则：
Windows不用设置。
linux可以选择：O_DIRECT
直接写入磁盘，禁止系统Cache了
设置方法：在my.cnf文件里：
innodb_flush_method=O_DIRECT

innodb_max_dirty_pages_pct buffer pool缓冲中

作用：在buffer pool缓冲中，允许Innodb的脏页的百分比，值在范围1-100,默认为90，建议保持默认。
这个参数的另一个用处：当Innodb的内存分配过大，致使Swap占用严重时，可以适当的减小调整这个值，使达到Swap空间释放出来。建义：这个值最大在90%，最小在15%。太大，缓存中每次更新需要致换数据页太多，太小，放的数据页太小，更新操作太慢。
设置方法：在my.cnf文件里：
innodb_max_dirty_pages_pct＝90
动态更改需要有管理员权限：
set global innodb_max_dirty_pages_pct=50;

5）公共参数调优
skip-external-locking
MyISAM存储引擎也同样会使用这个参数，MySQL4.0之后，这个值默认是开启的。
作用是避免MySQL的外部锁定(老版本的MySQL此参数叫做skip-locking)，减少出错几率增强稳定性。建议默认值。
设置方法，在my.cnf文件里：
skip-external-locking
skip-name-resolve
禁止MySQL对外部连接进行DNS解析（默认是关闭此项设置的，即默认解析DNS），使用这一选项可以消除MySQL进行DNS解析的时间。
但需要注意，如果开启该选项，则所有远程主机连接授权都要使用IP地址方式，否则MySQL将无法正常处理连接请求！如果需要，可以设置此项。
设置方法，在my.cnf文件里：（我这线上mysql数据库中打开了这一设置）
skip-name-resolve
max_connections
设置最大连接（用户）数，每个连接MySQL的用户均算作一个连接，max_connections的默认值为100。此值需要根据具体的连接数峰值设定。
设置方法，在my.cnf文件里：
max_connections = 3000
query_cache_size
查询缓存大小，如果表的改动非常频繁，或者每次查询都不同，查询缓存的结果会减慢系统性能。可以设置为0。
设置方法，在my.cnf文件里：
query_cache_size = 512M
sort_buffer_size
connection级的参数，排序缓存大小。一般设置为2-4MB即可。
设置方法，在my.cnf文件里：
sort_buffer_size = 1024M
read_buffer_size
connection级的参数。一般设置为2-4MB即可。
设置方法，在my.cnf文件里：
read_buffer_size = 1024M
max_allowed_packet
网络包的大小，为避免出现较大的网络包错误，建议设置为16M
设置方法，在my.cnf文件里：
max_allowed_packet = 16M
table_open_cache
当某一连接访问一个表时，MySQL会检查当前已缓存表的数量。如果该表已经在缓存中打开，则会直接访问缓存中的表，以加快查询速度；如果该表未被缓存，则会将当前的表添加进缓存并进行查询。
通过检查峰值时间的状态值Open_tables和Opened_tables，可以决定是否需要增加table_open_cache的值。
如果发现open_tables等于table_open_cache，并且opened_tables在不断增长，那么就需要增加table_open_cache的值;设置为512即可满足需求。
设置方法，在my.cnf文件里：
table_open_cache = 512
myisam_sort_buffer_size
实际上这个myisam_sort_buffer_size参数意义不大，这是个字面上蒙人的参数，它用于ALTER TABLE, OPTIMIZE TABLE, REPAIR TABLE 等命令时需要的内存。默认值即可。
设置方法，在my.cnf文件里：
myisam_sort_buffer_size = 8M
thread_cache_size
线程缓存，如果一个客户端断开连接，这个线程就会被放到thread_cache_size中（缓冲池未满），SHOW STATUS LIKE 'threads%';如果 Threads_created 不断增大，那么当前值设置要改大，改到 Threads_connected 值左右。（通常情况下，这个值改善性能不大），默认8即可
设置方法，在my.cnf文件里：
thread_cache_size = 8
innodb_thread_concurrency
线程并发数，建议设置为CPU内核数*2
设置方法，在my.cnf文件里：
innodb_thread_concurrency = 8


－影响InnoDB性能的一些重要参数－－－－－－－－－－－－－－
1）InnoDB_buffer_pool_size
这个参数定义InnoDB存储引擎的表数据和索引数据的最大内存缓冲区,InnoDB_buffer_pool_size参数同时提供为数据块和索引块做缓存.这个值设置的越高,访问表中数据需要的磁盘IO就越少.
2）InnoDB_flush_log_at_trx_commit
这个参数控制缓冲区的数据写入到日志文件以及日志文件数据刷新到磁盘的操作时机.在正式环境中建议设置成1。
设置0时日志缓冲每秒一次被写到日志文件,并且对日志文件做向磁盘刷新的操作,但是在一个事物提交不做任何操作.
设置1时在每个事物提交时,日志缓冲被写到日志文件,并且对日志文件做向磁盘刷新的操作
设置2时在每个事物提交时,日志缓冲被写到日志文件,但不对日志文件做向磁盘刷新的操作,对日志文件每秒向磁盘做一次刷新操作.
3）InnoDB_additional_mem_pool_size
这个参数是InnoDB用来存储数据库结构和其他内部数据结构的内存池.应用程序的表越多,则需要从这里分配越多的内存,如果用光这个池,则会从OS层分配.
4）InnoDB_lock_wait_timeout
这个参数自动检测行锁导致的死锁并进行相应处理,但是对于表锁导致的死锁不能自动检测默认值为50秒.
5）InnoDB_support_xa
这个参数设置MySQL是否支持分布式事务
6）InnoDB_log_buffer_size
这个参数日志缓冲大小
7）InnoDB_log_file_size
这个参数是一个日志组中每个日志文件的大小,此参数在高写入负载尤其是大数据集的情况下很重要.这个值越大则性能相对越高,但好似副作用是一旦系统崩溃恢复的时间会加长.
8）Innodb_io_capacity
这个参数刷新脏页数量和合并插入数量，改善磁盘IO处理能力
9）Innodb_use_native_aio
异步I/O在一定程度上提高系统的并发能力，在Linux系统上，可以通过将MySQL的服务器此参数的值设定为ON设定InnoDB可以使用Linux的异步I/O子系统.
10）Innodb_read_io_threads
这个参数可调整的读请求的后台线程数
11）Innodb_write_io_threads
这个参数可调整的写请求的后台线程数
12）InnoDB_buffer_pool_instances
这个参数能较好的运行于多核处理器，支持使用 此参数对服务器变量建立多个缓冲池实例，每个缓冲池实例分别自我管理空闲列表、列表刷写、LRU以及其它跟缓冲池相关的数据结构，并通过各自的互斥锁进行保护
13）InnoDB_purge_threads
MySQL5.5以前碎片回收操作是主线程的一部分，这经定期调度的方式运行，但会阻塞数据库的其他操作.到5.5以后，可以将这个线程独立出来 ；这个能让碎片回收得更及时而且不影响其他线程的操作
14）Innodb_flush_method
这个参数控制着innodb数据文件及redo log的打开、刷写模式，对于这个参数，文档上是这样描述的：
有三个值：fdatasync(默认)，O_DSYNC，O_DIRECT
默认是fdatasync，调用fsync()去刷数据文件与redo log的buffer
为O_DSYNC时，innodb会使用O_SYNC方式打开和刷写redo log,使用fsync()刷写数据文件
为O_DIRECT时，innodb使用O_DIRECT打开数据文件，使用fsync()刷写数据文件跟redo log
总结一下三者写数据方式：
fdatasync模式：写数据时，write这一步并不需要真正写到磁盘才算完成（可能写入到操作系统buffer中就会返回完成），真正完成是flush操作，buffer交给操作系统去flush,并且文件的元数据信息也都需要更新到磁盘。
O_DSYNC模式：写日志操作是在write这步完成，而数据文件的写入是在flush这步通过fsync完成
O_DIRECT模式：数据文件的写入操作是直接从mysql innodb buffer到磁盘的，并不用通过操作系统的缓冲，而真正的完成也是在flush这步,日志还是要经过OS缓冲
使用下面命令就可以查看到上面参数的设置：
mysql> show variables like "%innodb%";

Sql优化
非范围查询适当使用Hash索引比btree更快
适用于非范围查询。。很多查询属于非范围查询

适当合并sql 需要确保不会死锁的情况下

ohter
配置缩短数据库表事务锁定时间 加快响应时间


升级到mysql8  性能优化了很多
Mysql 5.7  和8版本已经优化了很多性能问题。。

MySQL 5.7 新特性详解 
MySQL 5.7.9 是目前世界上最流行开源数据库的一令人兴奋的新版本， 比 MySQL 5.6 快 3 倍，同时还提高了可用性，可管理性和安全性。一些重要的增强功能如下： 

性能和可扩展性：改进 InnoDB 的可扩展性和临时表的性能，从而实现更快的网络和大数据加载等操作。

优化: 我们重写了大部分解析器，优化器和成本模型。这提高了可维护性，可扩展性和性能。

InnoDB 读写扩展。改善了数据库的读写负载性能。移除了 InnoDB 的索引死锁(WL#6363, WL#6326)。现在的索引锁被替换成更加精细的树的“块锁
InnoDB 更快的并行数据刷新。扫描刷新一批队列数据的时候，减少了需要检索的页面数目，从而提高了页面更新的速度(WL#7047)。检索的时间复杂度已经从 O(n*n) 降低到了 O(n)。与此同时，利用多线程的多页清除技术实现了并行的数据刷新(WL#6642)。这使得数据库在多核系统上的扩展性和吞吐量均大大得到增强的同时，避免了数据刷新成为瓶颈。最后，改善了自适应的刷新算法以及其他相关机制，来达到更加一致和平滑的吞吐量。

加载块数据的性能的提升。为了创建索引所进行的块数据的加载，（WL#7277）。通过实现块数据的索引排序，从而加速了 CREATE INDEX 运算操作符的实现。在此之前，InnoDB 循环遍历基表，为每访问一次基表里的每条记录创建一个索引。在此次更新之后，InnoDB 可以一次从基表读取多条记录，并且通过索引的键值排序这些记录，从而由单次的块操作下创建出一整块记录的索引集。

InnoDB 临时表性能
优化普通 SQL 临时表性能是 5.7 的目标之一。首先，我们通过避免持久化临时表到磁盘时的不必要的步骤，使得临时表的创建和移除成为一个轻量级的操作。我们将临时表移动到一个单独的表空间(WL#6560) ，因此对于临时表的恢复过程就变成了一个在启动时仅仅简单的重新创建临时表的单一的无状态步骤。我们去掉了临时表中不必要的持久化(WL#6469)。临时表仅仅在连接/会话内可见，创建它们，通过服务的生命周期绑定它们。我们通过移除不必要的 UNDO 和 REDO 日志，改变缓冲和锁，从而为临时表优化了 DML(WL#6470) 。我们增加了 UNDO 日志的一个额外的类型 (WL#6915)，这个类型是不可 REDO 日志和保留在一个新的单独的临时表空间。这些 non-redo-logged UNDO 日志在恢复期间不需要，仅在回滚操作是需要。
第二，我们也为临时表设定了一个特别类型，我们称之为“内在临时表”(WL#7682, WL#6711)。内在临时表和普通临时表很像，只是内在临时表使用宽松的 ACID 和 MVCC 语义。目的是为了支持内部模块的内部用例， 例如，优化器为了中间操作而要求轻型和超快速的表。那么我们就让优化器使用 InnoDB 的“内在临时表”作为内部储存(WL#6711)。最终，我们让 InnoDB 的默认引擎使用 内部临时表 。见 Krunal Bauskar 的文章“MySQL 5.7: InnoDB 内在表“。
 1
 
缓冲池 —— 卸载和加载
我们改进了缓冲池卸载和加载场景(WL#6504)。目前可以卸载每个缓冲池中仅最热的 N％ 页。加载操作减少了对用户活动的破坏性，因为现在的加载是在后台为客户提供服务的；也不会尝试着太据有侵略性和从服务新的客户请求中占据太多的 IO 资源。见 Tony Darnell 的文章 “MySQL 卸载和加载InnoDB 缓冲池“。
我们也通过默认和改变默认百分比到 25% 的方式改变服务器使用缓冲池加载和卸载 (WL#8317)。这也使得在 1. 支持“热”工作数据设置和 2. 关闭和启动次数之间形成好的默认平衡。
MySQL 8.0新特性全面认识
7、优化
不可见索引，开始支持invisible index，(感觉又和Oracle一样了)，在优化SQL的过程中可以设置索引为不可见，优化器变不会利用不可见索引
支持降序索引，可以对索引定义 DESC，之前，索引可以被反序扫描，但影响性能，而降序索引就可以高效的完成
13、直方图
MySQL 8.0 版本开始支持期待已久直方图。优化器会利用column_statistics的数据，判断字段的值的分布，得到更准确的执行计划。
可以使用 ANALYZE TABLE table_name [UPDATE HISTOGRAM on col_name with N BUCKETS |DROP HISTOGRAM ON  clo_name] 来收集或者删除直方图信息
14、支持会话级别SET_VAR 动态调整部分参数，有利于提升语句性能。
select /*+ SET_VAR(sort_buffer_size = 16M) */ id  from test order id ;
insert  /*+ SET_VAR(foreign_key_checks=OFF) */ into test(name) values(1);
15、默认参数的调整
调整back_log的默认值，保持和 max_connections一致，增强突发流量带来的连接处理容量。
修改 event_scheduler 默认为ON，之前默认是关闭的。
调整max_allowed_packet 的默认值，从4M增加到64M。
调整bin_log,log_slave_updates默认值为on。
调整expire_logs_days的过期时间为30天，老版本是7天，生产环境时，检查该参数，防止binlog过多造成空间紧张。
调整innodb_undo_log_truncate 默认为ON
调整innodb_undo_tablespaces 默认值为2
调整innodb_max_dirty_pages_pct_lwm 默认值10
调整innodb_max_dirty_pages_pct默认值为90
新增innodb_autoinc_lock_mode 默认值为2
16、InnoDB性能提升
废除buffer pool mutex,将原来一个mutex拆分成多个，提高并发
拆分LOCK_thd_list 和 LOCK_thd_remove 这两个mutex，大约可提高线程链接效率5%。
17、行缓存
 MySQL8.0的优化器可以估算将要读取的行数，因此可以提供给存储引擎一个合适大小的row buffer来存储需要的数据。大批量的连续数据扫描的性能将受益于更大的record buffer
18、改进扫描性能
改进InnoDB范围查询的性能，可提升全表查询和范围查询 5-20%的性能。
19、成本模型
InnoDB缓冲区可以估算缓存区中的有多少表和索引，这可以让优化器选择访问方式时知道数据是否可以存储在内存中还是必须存储到磁盘上。


数据库连接池 配置立即释放 防止过长事务和死锁连接
配置事务最长时间

配置锁定类对参数，调小锁等待间隔
 innodb_deadlock_detect，也即 死锁自动监测机制时

调小间隔 innodb_deadlock_detect

innodb_lock_wait_timeout，该参数指定了“锁申请时候的最长等待时间”
官方的解释是：The length of time in seconds an InnoDB transaction waits for a row lock before giving up.
innodb_lock_wait_timeout默认值是50秒，也就是意味着session请求时，申请不到锁的情况下最多等待50秒钟

innodb_rollback_on_timeout
这里就涉及到另外一个参数：innodb_rollback_on_timeout，默认值是off，该参数的决定了当前请求锁超时之后，回滚的是整个事物，还是仅当前语句，
官方的解释是：InnoDB rolls back only the last statement on a transaction timeout by default。
默认值是off，也就是回滚当前语句（放弃当前语句的锁申请），有人强烈建议打开这个选项（on），也就是一旦锁申请超时，就回滚整个事物

任意一个session出现锁超时，放弃当前的语句申请的锁，而不是整个事物持有的锁，当前session并不释放其他session请求的锁资源，
即便是继续下去，依旧如此，两者又陷入了相互等待，相互锁请求超时，继续死循环。
从这里可以看到，与死锁自动检测机制在发现死锁是主动选择一个作为牺牲品不同，一旦关闭了innodb_deadlock_detect，Session中的任意一方都不会主动释放已经持有的锁。
此时如果应用程序如果不足够的健壮，继续去申请锁（比如重试机制，尝试重试相关语句），session双方会陷入到无限制的锁超时死循环之中。

这只不过是一个典型的负面场景，除此之外，还会有哪些问题值得思考？
1，因为事物无法快速提交或者回滚，那么连接持有的时间会增加，一旦并发量上来，连接数可能成为一个问题。
2，锁超时时间肯定要设置为一个相对较小的时间，但具体又设置为多少靠谱。
 4，面对锁超时，应用程序端如何合理地处理锁超时的情况，是重试还是放弃。
5，与此关联的innodb_rollback_on_timeout如何设置，是保持默认的关闭（锁超时的情况下，取消当前语句的所申请），还是打开（锁超时的情况下，回滚整个事物）

单独实例
对彩票类设置单独数据库实例，直播类等其他项目放在另外db实例防止互相影响
更高的iops
 数据库大量随机读写io，如果能使用ssd最好了 或者更高性能的存储
Sql优化  索引优化 

 
配置全面使用db数据库的cache机制
全面调整mysql的cache类参数
各种buffer pool cache类的参数加大

innodb_buffer_pool_size 等
innodb_log_buffer_size
thread_pool_priority 类对参数
适当开启query cache
cantuse innodb_flush_method=O_DIRECT  避免双缓存 提升响应速度
(该参数需要重启mysql实例起效)
控制innodb数据文件和redo log的打开、刷写模式。有三个值：fdatasync(默认)，O_DSYNC，O_DIRECT。
fdatasync模式：写数据时，write这一步并不需要真正写到磁盘才算完成（可能写入到操作系统buffer中就会返回完成），真正完成是flush操作，buffer交给操作系统去flush,并且文件的元数据信息也都需要更新到磁盘。
O_DSYNC模式：写日志操作是在write这步完成，而数据文件的写入是在flush这步通过fsync完成。
O_DIRECT模式：数据文件的写入操作是直接从mysql innodb buffer到磁盘的，并不用通过操作系统的缓冲，而真正的完成也是在flush这步,日志还是要经过OS缓冲。
三种模式如下图： 通过图可以看出O_DIRECT相比fdatasync的优点是避免了双缓冲，本身innodb buffer pool就是一个缓冲区，不需要再写入到系统的buffer，但是有个缺点是由于是直接写入到磁盘，所以相比fdatasync的顺序读写的效率要低些。
在大量随机写的环境中O_DIRECT要比fdatasync效率更高些

启用修改延迟法 cache法 提升insert类的性能 Insert delay 
Update 使用insert 零时表+定时机制解决

Cache 事务日志配置

innodb_flush_log_at_trx_commit=0
innodb_flush_log_at_trx_commit 取值为 0 的时候，log buffer 会 每秒写入到日志文件并刷写（flush）到磁盘。但每次事务提交不会有任何影响，也就是 log buffer 的刷写操作和事务提交操作没有关系。在这种情况下，MySQL性能最好，但如果 mysqld 进程崩溃，通常会导致最后 1s 的日志丢失。
当取值为 1 时，每次事务提交时，log buffer 会被写入到日志文件并刷写到磁盘。这也是默认值。这是最安全的配置，但由于每次事务都需要进行磁盘I/O，所以也最慢。
当取值为 2 时，每次事务提交会写入日志文件，但并不会立即刷写到磁盘，日志文件会每秒刷写一次到磁盘。这时如果 mysqld 进程崩溃，由于日志已经写入到系统缓存，所以并不会丢失数据；在操作系统崩溃的情况下，通常会导致最后 1s 的日志丢失。
是否有延迟索引机制

延迟更新索引

使用内存表存储引擎 做更新cache
适当使用临时表机制
适当使用分区机制
Otehr


innodb_concurrency_tickets
確定可以同時進入 的線程數 InnoDB。如果線程InnoDB數已達到並發限制，則在嘗試輸入線程時會將其置於隊列中。當允許線程進入時 InnoDB，會給它一個等於的值 的“ 票證”innodb_concurrency_tickets，線程可以InnoDB 自由進入和離開，直到用完票證為止。在那之後，線程在下一次嘗試進入時再次受到並發檢查（可能的排隊） InnoDB。默認值為5000。
用一個小 innodb_concurrency_tickets 值，僅需要處理幾排小事務需要處理大量行大交易公平競爭。較小innodb_concurrency_tickets 值的缺點 是大型事務必須先在隊列中循環多次才能完成，這延長了完成任務所需的時間。
innodb_concurrency_tickets 值 較大時 ，大型事務花費較少的時間等待隊列末尾的位置（由控制 innodb_thread_concurrency），而花費更多的時間檢索行。大型事務還需要通過隊列的行程減少以完成任務。較大innodb_concurrency_tickets 值的缺點 是，同時運行的大型事務太多，會使較小的事務等待更長的時間才能執行，從而使較小的事務餓死。
對於非零 innodb_thread_concurrency 值，您可能需要innodb_concurrency_tickets 向上或向下調整該 值，以在較大和較小的交易之間找到最佳平衡。該SHOW ENGINE INNODB STATUS報告顯示了當前通過隊列的執行交易中剩餘的票證數量。該數據也可以從 表的 TRX_CONCURRENCY_TICKETS列中獲得 INFORMATION_SCHEMA.INNODB_TRX。

ref
（impt not read cmplt）MySQL 优化系列（1）-- InnoDB重要参数优化 - 散尽浮华 - 博客园
MySQL 优化系列（1）-- InnoDB重要参数优化 - 散尽浮华 - 博客园
Atitit 数据库提升性能的机制总结db perf enhance v2 ubb.docx



