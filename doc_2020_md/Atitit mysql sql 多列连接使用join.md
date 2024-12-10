Atitit mysql sql 多列连接使用join

貌似不能使用后子查询链接  多列一行


select   t.id,t1.* from (select 1 id ) t left join (select 1 id,3 age,55 name)  t1 on t.id=t1.id


通用查询数据接口 新增 编辑接口  脚本接口复杂逻辑处理接口 与brain联调足球比赛比分接口
