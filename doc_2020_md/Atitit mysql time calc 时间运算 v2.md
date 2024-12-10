Atitit mysql time calc 时间运算



from_unixtime

当天起点时间戳

select from_unixtime( unix_timestamp (date(now())) )
2020-05-22 00:00:00


过去8小时
select  date_sub(now(),   interval 8 hour)

比较两个datetime类型的时间间隔，以秒为单位：

原来，TIME_TO_SEC只会把datetime数据的time部分转化为秒数，不会关心date谁大谁小，所以要比较两个datetime数据，先得TimeDiff一下，再转化为秒数，即开头写的：
SELECT TIME_TO_SEC(TIMEDIFF('2009-02-09 11:24:46','2009-02-09 10:23:46'));
————————————————
版权声明：本文为CSDN博主「电灯泡」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/xukunddp/article/details/20848843

