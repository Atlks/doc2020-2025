Atitit 数据库性能分析参数分析


大 鱼, [17.12.20 19:42]
--  提升响应速度的参数
show global variables like '%tx_isolation%';
 show global variables like '%innodb_flush_log_at_trx_commit%';

大 鱼, [17.12.20 19:42]
--  重要cache类参数 
 show global variables like '%innodb_buffer_pool_size%';
 show global variables like '%innodb_log_buffer_size%';

大 鱼, [17.12.20 19:44]
刚才本机测试了下几个重要参数，大量insert update修改类提升很明显。。我问阿灿，他说线上数据库参数调整貌似只调整了个隔离级别和 最大线程数

大 鱼, [17.12.20 19:45]
本机写了个测试一个insert任务从20s直接提升到2s

大 鱼, [17.12.20 19:46]
所以如果数据库参数是默认的话，可以大力调整的

大 鱼, [18.12.20 12:54]
还有些  多线程类的参数 ，默认会比较低，服务器cpu核心数应该会比较多，，也可能需要调整。。
-- multi类  多线程类的参数

 show global variables like '%thread%';

 show global variables like '%conn%';
 show global variables like '%concurrency%'
 show global variables like '%innodb_io_capacity%';
 show global variables like '%innodb_buffer_pool_instances%';
