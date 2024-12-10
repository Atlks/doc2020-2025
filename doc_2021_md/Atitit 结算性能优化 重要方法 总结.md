Atitit 结算性能优化 重要方法 总结

加快响应
Mongodb
去orm框架 在批量速度下
升级jdk mysql驱动  mysql
存储过程
查询缓存
Mysql 查询缓存20%
Mybatis查询缓存 更加精细些。。

多线程
Go协程
Sql批处理（有效） allowMultiQueries=true 

大约6倍提升



批处理 rewriteBatchedStatements=true
关于rewriteBatchedStatements这个参数介绍：
MySQL的JDBC连接的url中要加rewriteBatchedStatements参数，并保证5.1.13以上版本的驱动，才能实现高性能的批量插入。
MySQL JDBC驱动在默认情况下会无视executeBatch()语句，把我们期望批量执行的一组sql语句拆散，一条一条地发给MySQL数据库，批量插入实际上是单条插入，直接造成较低的性能。
只有把rewriteBatchedStatements参数置为true, 驱动才会帮你批量执行SQL
另外这个选项对INSERT/UPDATE/DELETE都有效
添加rewriteBatchedStatements=true这个参数后的执行速度比较：
同个表插入一万条数据时间近似值：
JDBC BATCH 1.1秒左右 > Mybatis BATCH 2.2秒左右 > 拼接SQL 4.5秒左右


