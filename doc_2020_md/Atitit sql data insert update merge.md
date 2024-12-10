Atitit sql data insert update merge



Repalce   all  (update all

 ON DUPLICATE KEY UPDATE    (update part
Insert ingore


4、将stu1表中的一些数据更新到stu2表中.(stu1表和stu2表的字段名称可以不同)
update stu1 t,stu2 tt set tt.Sno = t.Sno,tt.Sname = t.Sname,tt.Ssex = t.Ssex,tt.Sag

merge
2.2. INSERT INTO … ON DUPLICATE KEY UPDATE 推荐，保留原值	1

INSTEAD OF INSERT触发器（不推荐）
Mysql不支持
merge sql语句 
mysql不支持（推荐）

2.1. 联合索引判断法 最简单	1
2.3. INSTEAD OF INSERT触发器（不推荐）	2

Batch insert

2. replace into tbl_name(col_name, ...) select ...
Atitit table copy表复制 sql  batch insert


Ref
Atitit 数据同步merge  最佳实践 流程 如果存在就更新,否则新建v4 s36
