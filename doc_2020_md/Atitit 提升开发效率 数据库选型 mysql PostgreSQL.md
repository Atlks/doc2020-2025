Atitit 提升开发效率 数据库选型 mysql PostgreSQL 

Json支持更好，可以把数据转换为json子查询
PostgreSQL异步提交（Asynchronous Commit）的功能：
　 这个功能oracle中也是到oracle11g R2才有的功能。因为在很多应用场景中，当宕机时是允许丢失少量数据的，这个功能在这样的场景中就特别合适。在PostgreSQL9.0中把 synchronous_commit设置为false就打开了这个功能。需要注意的是，虽然设置为了异步提交，当主机宕机时，PostgreSQL只会 丢失少量数据，异步提交并不会导致数据损坏而数据库起不来的情况。MySQL中没有听说过有这个功能。
2. 与PostgreSQl配合的开源软件很多，有很多分布式集群软件，如pgpool、pgcluster、slony、plploxy等等，很容易做读写分离、负载均衡、数据水平拆分等方案，而这在MySQL下则比较困难。
3. PostgreSQL源代码写的很清晰，易读性比MySQL强太多了，怀疑MySQL的源代码被混淆过。所以很多公司都是基本PostgreSQL做二次开发的。
4. PostgreSQL在很多方面都比MySQL强，如复杂SQL的执行、存储过程、触发器、索引。同时PostgreSQL是多进程的，而MySQL是线 程的，虽然并发不高时，MySQL处理速度快，但当并发高的时候，对于现在多核的单台机器上，MySQL的总体处理性能不如PostgreSQL，原因是 MySQL的线程无法充分利用CPU的能力。
