Atitit 应用层索引引擎对实现

Mysql保存为json字符串，应用层索引定时器扫描此表，增加一个xx_index的表，记录index状态。

如果没有索引的，那么建立索引。。

colVal,rowid
12,rowid1
13,rowid2


Search by search..firest search this index tab..得到pklist ，然后按照pk查询组合即可。

或者使用事件触发，生成一个文件io，，每次检查文件就可以了。。类似于文件lock锁。。不占用数据库连接。。
使用内存。Rds也可。。Mq模式
