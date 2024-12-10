Atitit mysql性能优化 超多表


open_files_limit

TechTarget中国原创内容，原文链接： https://searchdatabase.techtarget.com.cn/7-21559/
© TechTarget中国：https://www.techtarget.com.cn


# table cache performance settings #
table_open_cache = 4096    //指定表高速缓存的大小。每当MySQL访问一个表时，如果在表缓冲区中还有空间，该表就被打开并放入其中，这样可以更快地访问表内容
table_definition_cache = 4096    //表定义信息缓存
table_open_cache_instances = 64    //指的是 MySQL 缓存 table 句柄的分区的个数，而每一个 cache_instance 可以包含不超过table_open_cache/table_open_cache_instances 的table_cache_element


innodb_log_file_size = 200M    //日志组的大小,默认为5M；如果对 Innodb 数据表有大量的写入操作，那么选择合适的 innodb_log_file_size值对提升MySQL性能很重要。然而设置太大了，就会增加恢复的时间，因此在MySQL崩溃或者突然断电等情况会令MySQL服务器花很长时间来恢复
innodb_log_files_in_group = 2    //日志组的数量，默认为2
innodb_log_buffer_size = 16M    //日志缓冲池的大小
innodb_purge_threads = 4    //在innodb 1.2版本开始 innodb支持多个purge thread 这样做的目的是为了进一步加快undo页的回收这样也能更进一步利用磁盘的随机读取性能 用户可以设置4个purge thread


innodb_sort_buffer_size = 67108864    //加速ORDER BY 或者GROUP BY 操作

