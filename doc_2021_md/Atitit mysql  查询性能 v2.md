Atitit  mysql 查询性能 提升 


对于MySQL配置项，有的配置项是对于一个线程而言的(即为每个线程分配的资源,包括sort_buffer_size,join_buffer_size,read_buffer_size,read_rnd_buffer_size是为每个连接线程分配的内存大小)，因此要充分估计MySQL的负载。

索引 

Query cache

query_cache_size：缓存MySQL中的ResultSet，也就是一条SQL语句执行的结果集，所以仅仅只能针对select语句。当某个表的数据有任何任何变化，都会导致所有引用了该表的select语句在Query Cache中的缓存数据失效。所以，当我们的数据变化非常频繁的情况下，使用Query Cache可能会得不偿失。根据命中率(Qcache_hits/(Qcache_hits+Qcache_inserts)*100))进行调整，一般不建议太大，256MB可能已经差不多了，大型的配置型静态数据可适当调大.
可以通过命令show status like 'Qcache_%'查看目前系统Query catch使用大小
 
read_buffer_size：MySql读入缓冲区大小。对表进行顺序扫描的请求将分配一个读入缓冲区，MySql会为它分配一段内存缓冲区。如果对表的顺序扫描请求非常频繁，可以通过增加该变量值以及内存缓冲区大小提高其性能
 
sort_buffer_size：MySql执行排序使用的缓冲大小。如果想要增加ORDER BY的速度，首先看是否可以让MySQL使用索引而不是额外的排序阶段。如果不能，可以尝试增加sort_buffer_size变量的大小
 
read_rnd_buffer_size：MySql的随机读缓冲区大小。当按任意顺序读取行时(例如，按照排序顺序)，将分配一个随机读缓存区。进行排序查询时，MySql会首先扫描一遍该缓冲，以避免磁盘搜索，提高查询速度，如果需要排序大量数据，可适当调高该值。但MySql会为每个客户连接发放该缓冲空间，所以应尽量适当设置该值，以避免内存开销过大。
 
record_buffer：每个进行一个顺序扫描的线程为其扫描的每张表分配这个大小的一个缓冲区。如果你做很多顺序扫描，可能想要增加该值
 
thread_cache_size：保存当前没有与连接关联但是准备为后面新的连接服务的线程，可以快速响应连接的线程请求而无需创建新的
 
table_cache：类似于thread_cache_size，但用来缓存表文件，对InnoDB效果不大，主要用于MyISAM



一、group by
当我们执行 group by 操作在没有合适的索引可用的时候，通常先扫描整个表提取数据并创建一个临时表，然后按照 group by 指定的列进行排序。在这个临时表里面，对于每一个 group 的数据行来说是连续在一起的。完成排序之后，就可以发现所有的 groups，并可以执行聚集函数（aggregate function）。可以看到，在没有使用索引的时候，需要创建临时表和排序。在执行计划中通常可以看到“Using temporary; Using filesort”。



覆盖索引
当使用 Select 的数据列只用从索引中取得，而不必从数据表中读取，换句话说查询列要被所使用的索引覆盖。
例如：User 表中将 LastName 作为索引。如果写以下查询语句：
Select LastName from user 
LastName 及作为索引，又在查询内容中显示出来，那么 LastName 就是覆盖索引。
覆盖索引是高效查找行方法，通过索引就可以读取数据，就不需要再到数据表中读取数据了。
而且覆盖索引会以 Usingindex 作为标示，可以通过 Explain 语句查看。

Explain 查看覆盖索引标示
覆盖索引主要应用在 Count 等一些聚合操作上，提升查询的效率。例如上面提到的 Selectcount(LastName) from user 就可以把 LastName 设置为索引。
还有可以进行列查询的回表优化，如下：
Select LastName, FirstName from user where LastName=‘Jack’ 
如果此时 LastName 设置为索引，可以将 LastName 和 FirstName 设置为多列索引(联合索引)。
避免回表行为的发生。这里的回表是指二级索引搜索到以后，再找到聚合索引，然后在查找 PK 的过程。
这里需要通过两次搜索完成。简单点说就是使用了覆盖索引以后，一次就可以查到想要的记录，不用在查第二次了。


②GROUPBY 优化
MySQL 通过索引来优化 GROUPBY 查询。在无法使用索引的时候，会使用两种策略优化：临时表和文件排序分组。
可以通过两个参数 SQL_BIG_RESULT 和 SQL_SMALL_RESULT 提升其性能。
这两个参数只对 Select 语句有效。它们告诉优化器对 GROUPBY 查询使用临时表及排序。
SQL_SMALL_RESULT 告诉优化器结果集会很小，可以将结果集放在内存中的索引临时表，以避免排序操作。
如果是 SQL_BIG_RESULT，则告诉优化器结果集可能会非常大，建议使用磁盘临时表做排序操作。
例如：
SelectSQL_BUFFER_RESULTfield1, count(*) from table1 groupby field1 
假设两个表做关联查询，选择查询表中的标识列(主键)分组效率会高。
例如 actor 表和 film 表通过


确定MySQL会为每个连接使用多少内存，比如排序缓冲区和临时表(要充分估计最大连接数，如sort_buffer_size,join_buffer_size,read_buffer_size,read_rnd_buffer_size)



(3)表缓存

table_open_cache:打开表的缓存数


作用：为打开的表设置缓存，如果之后打开同名的表，可以从缓存中直接取出，不用直接再打开


推荐值：不断观察open_tables这个状态值来决定其大小。


table_definition_cache：表定义缓存数


作用：为表的结构定义建立缓存,存放的表的结构定义信息


推荐值：根据表的数据来决定(最大为表的数量，当然最好是常用的表)


