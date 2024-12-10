Atitit 提升mysql 数据库查询性能 总结


索引

物化视图机制 （定时更新
可用零食表实现物化视图功能。。 定时调度刷新数据
Create  TABLE tmp_foot_match_v_all  select *,from_unixtime(match_time) from foot_match_v_all

增量更新使用insert from
批量删除过期数据

根据ui调整表结构 合并表
可用触发器同步模式
