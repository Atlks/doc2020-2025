Atitit 数据库查询缓存mysql query cache


性能提升约20%-30%
短期大批量查询还是很有效的，。短期内更新类操作会比较少

开启必须要修改配置文件

 query_cache_type=1


显示缓存状态
show global variables like '%query_cache%';

show global status like '%qcache%'


调整参数化，
可以根据缓存状态来调整参数

-- cache  
set global  query_cache_type=1;
set global query_cache_limit=10234;  -- 10M per rsult size limit
set global  query_cache_size=800123456;


评估缓存命中率与缓存状态
在开奖测试中，缓存命中率约50%
Qcache_hits	缓存命中次数
Qcache_inserts	3479418


show global status like '%qcache%'


Qcache_free_memory	291983080
Qcache_hits	17403131
Qcache_inserts	3479418
Qcache_lowmem_prunes	37775
Qcache_not_cached	8465586
Qcache_queries_in_cache	158587
Qcache_total_blocks	318561



3.失效机制：

    当后端任何一个表的一条数据，索引，结构发生变化时，就会将与此表关联的query chache失效，并且释放内存。所以对于数据变化频繁的sql就不要cache了。那样不但不会提高性能还能得到相反的结果，因为每次多了查询缓存的操作。
    这里要指出的是，这种失效机制并不科学，因为有些表的改动并不会导致结果集的改变。但是这种方法简单，开销也比较小。
query_cache_limit：允许 Cache 的单条 Query 结果集的最大容量，默认是1MB，超过此参数设置的 Query 结果集将不会被 Cache


Query Cache 处理子查询：
   Query Cache 是以客户端请求提交的Query 为对象来处理的，只要客户端请求的是一个Query，无论这个 Query 是一个简单的单表查询还是多表 Join，亦或者是带有子查询的复杂 SQL，都被当作成一个Query，不会被分拆成多个Query 来进行Cache。所以，存在子查询的复杂Query 也只会产生一个Cache对象，子查询不会产生单独的Cache内容。UNION[ALL] 类型的语句也同样如此。

优化查询缓存
分拆多个子查询  让其可以进入cache
变化频繁的表使用内存表，雾化试图来cache
改写sql ，替换orm生产的sql为手工sql，方便分析和提前填充cache
