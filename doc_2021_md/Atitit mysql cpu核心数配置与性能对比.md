Atitit mysql cpu核心数配置与性能对比



此外，哪怕一个conn，mysql会使用所有的核心来处理。。。


机器是4核心。。但我无论配置为8还是4，性能差不多，都是18s更新类3w数据。。。


# 只能在配置文件里面调整，调整为cpu核心数
 innodb_read_io_threads = 4
innodb_write_io_threads = 4 



