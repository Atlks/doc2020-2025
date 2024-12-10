Atitit 线上服务器数据库迁移总结

统计分析数据库，行数，数据体积 大小


清理过大的体积数据表
目前100M以上的表直接清空会卡死，需要event定时delete模式比较好

导入sql时候去除readdata sql和约束检测

mysql - DETERMINISTIC, NO SQL, or READS SQL DATA in its declaration and binary logging i
修改definer模式 转换invoke模式，数据库内对象

