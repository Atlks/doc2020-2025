Atitit 表分区 按照日期

mysql的日期处理函数to_days()和from_days()
TO_DAYS(date)给出一个日期  date，返回一个天数(从 0 年开始的天数)：
mysql> SELECT TO_DAYS(950501); -> 728779 mysql> SELECT TO_DAYS('1997-10-07'); -> 729669
TO_DAYS() 无意于使用先于格里高里历法(即现行的阳历)(1582)出现的值，因为它不考虑当历法改变时所遗失的天数。



ALTER TABLE `cp`.`logx` PARTITION BY RANGE (to_days(dt2))
PARTITIONS 4
(
PARTITION `p202101222` VALUES LESS THAN (to_days('20210123')) MAX_ROWS = 0 MIN_ROWS = 0 ,
PARTITION `p20210123` VALUES LESS THAN (to_days('20210124')) MAX_ROWS = 0 MIN_ROWS = 0 ,
PARTITION `p20210124` VALUES LESS THAN (to_days('20210125')) MAX_ROWS = 0 MIN_ROWS = 0 ,
  PARTITION p11 VALUES LESS THAN (MAXVALUE) 

)
;

	insert logx set dt2=now();   

查看数据发布在哪个分区

 explain partitions 		select * from  logx  where dt2> STR_TO_DATE('2021-01-24','%Y-%m-%d') and  dt2< STR_TO_DATE('2021-01-25','%Y-%m-%d')   limit 100
		
(2)添加分区：与拆分分区
备注：不能超过p04的范围，严格递增每个分区，即最小不能小于前一个分区
下面新曾了两个分区n01和n02
 alter table titles
 reorganize partition p04 into(
 partition n01 values less than('1997-12-31'),
 partition n02 values less than('1998-12-31'),
 partition p04 values less than('2000-12-31')
 );
alter table logx add partition(partition p20210125  VALUES   LESS THAN (to_days('20210126'))   );



3、指定分区查询
select * from user PARTITION(p0);
