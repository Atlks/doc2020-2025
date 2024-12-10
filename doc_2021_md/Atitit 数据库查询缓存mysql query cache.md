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


