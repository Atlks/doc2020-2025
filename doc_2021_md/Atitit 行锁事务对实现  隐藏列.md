Atitit 行锁事务对实现  隐藏列


记录上的DB_TRX_ID系统隐藏列，获取事务ID trx_id。 ..

roll_pointer隐藏列    回滚指针

每一行都有2个隐藏列DATA_TRX_ID和DATA_ROLL_PTR(

删除标记位

隐式字段
对于InnoDB存储引擎，每一行记录都有两个隐藏列DB_TRX_ID、DB_ROLL_PTR，如果表中没有主键和非NULL唯一键时，则还会有第三个隐藏的主键列DB_ROW_ID。
DB_TRX_ID，记录每一行最近一次修改（修改/更新）它的事务ID，大小为6字节；
DB_ROLL_PTR，这个隐藏列就相当于一个指针，指向回滚段的undo日志，大小为7字节；
DB_ROW_ID，单调递增的行ID，大小为6字节；

3.1 三个隐藏字段
innoDB 向数据库中存储的每行添加三个隐藏字段（有的书上说是两个，但是我看官方文档说是三个）。

数据初始化.png
1 DB_TRX_ID 事务id
占6 字节，表示这一行数据最后插入或修改的事务id。此外删除在内部也被当作一次更新，在行的特殊位置添加一个删除标记（记录头信息有一个字节存储是否删除的标记）。
2 DB_ROLL_PTR 回滚指针
占7字节，回滚指针指向被写在Rollback segment中的undoLog记录，在该行数据被更新的时候，undoLog 会记录该行修改前内容到undoLog。
3 DB_ROW_ID 行ID
占7字节，他就项自增主键一样随着插入新数据自增。如果表中不存主键 或者 唯一索引，那么数据库 就会采用DB_ROW_ID生成聚簇索引。否则DB_ROW_ID不会出现在索引中。


