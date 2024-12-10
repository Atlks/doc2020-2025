Atitit 测试用例数据添加中用到的sql函数和内部变量总结

目录
1.1. 最后一条新加数据id主键LAST_INSERT_ID()	1
1.2. 得到当前时间戳（10位数字，精确到秒 ）， unix_timestamp(now())	1
1.3. 指定日期生成10位数字时间戳	1
1.4. 从10位数字时间戳得到日期	1
1.5. 日期运算加一天俩天  一周	1
1.6. 生成明天后天时间戳（十位数字格式）	2


最后一条新加数据id主键LAST_INSERT_ID()

使用last_insert_id
  SELECT LAST_INSERT_ID();

得到当前时间戳（10位数字，精确到秒 ）， unix_timestamp(now())
时间戳

指定日期生成10位数字时间戳
select   unix_timestamp('2020-05-09 13:13:13')

从10位数字时间戳得到日期 
date(  from_unixtime (1585407600))

日期运算加一天俩天  一周

select    date_add(now(), interval 1 day); - 加1天
select date_add(now(), interval 1 week);-加1周（7天

MySQL 为日期减去一个时间间隔：date_sub()

生成明天后天时间戳（十位数字格式）
select   unix_timestamp(date_add(now(), interval 1 day))  明天
select   unix_timestamp(date_add(now(), interval 2 day))    后天
