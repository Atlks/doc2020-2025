Atitit 数据库实现全局锁 分布式锁  存储过程


基于数据库：
基于数据库表做乐观锁，用于分布式锁。（version） 

基于数据库表做悲观锁（InnoDB，for update）

基于数据库表数据记录做唯一约束（表中记录方法名称）


MySQL存储过程 事务transaction
MySQL 中，单个 Store Procedure(SP) 不是原子操作，而 Oracle 则是原子的。如下的存储过程，即使语句2 失败，语句 1 仍然会被 commit 到数据库中：
 

