Atitit 数据库对比较 oracle  mysql pgsql
跨机器跨库mysql vs pgsql

fdw
外部数据源表，，pgsql很强大。。
dblink
动态增加列 pgzhichi



Cte


进程模式与线程模式的对比

PostgreSQL和oracle是进程模式，MySQL是线程模式。
进程模式对多CPU利用率比较高。
进程模式共享数据需要用到共享内存，而线程模式数据本身就是在进程空间内都是共享的，不同线程访问只需要控制好线程之间的同步。
线程模式对资源消耗比较少。
所以MySQL能支持远比oracle多的更多的连接。


堆表与索引组织表的的对比

Oracle支持堆表，也支持索引组织表
PostgreSQL只支持堆表，不支持索引组织表
Innodb只支持索引组织表


降序索引反向索引
PostgreSQL中索引的特色功能：
PostgreSQL中可以有部分索引，也就是只能表中的部分数据做索引，create index 可以带where 条件。同时PostgreSQL中的索引可以反向扫描，所以在PostgreSQL中可以不必建专门的降序索引了。

