Atitit insert插入数据

INSERT INTO SET这种方式可读性更好
insert into sys_country_t set name_zh='t',name_en='e',id=999,create_time=now(),delete_flag=0
方式4、INSERT INTO 表名 SET 列名1 = 列值1,列名2=列值2,...;（博友提供，感谢）
不过用INSERT INTO SET这种方式，不能批量增加数据



Merge融合插入


批量插入 INSERT INTO SELECT 语句
- INSERT INTO t_admin_rms_yhygwgxb select sys_guid(数据库


 SELECT ... INTO 语句
MySQL 数据库不支持 SELECT ... INTO 语句，但支持 INSERT INTO ... SELECT 。
