Atitit mysql timestamp 时间戳

函数now  别名
和current_timestamp 一个含义。。。
current_timestamp不带括号只能用在默认只里面
SYSDATE
Now  current_timestamp是字符串模式默认姐却岛秒
'2020-05-01 00:54:05'

提升精度 秒级别 毫秒 微妙

们尝试提升时间的精度，再次查看结果：spa
mysql> select NOW(6),CURRENT_TIMESTAMP(6),SYSDATE(6);
1
如上，咱们给这几个函数加上参数值，这个参数值表示秒后边的小数位数，此值最大为6，表示精确到微秒级别，默认为0，表示精确到秒。 
这时，咱们获得的结果是：code

字串模式vs文本模式
select UNIX_TIMESTAMP(current_timestamp(6)),UNIX_TIMESTAMP(),current_timestamp(6)

1585671740.946868	1585671740	2020-04-01 00:22:20.946868

UNIX_TIMESTAMP(current_timestamp(6))


不同
能够看到，NOW和CURRENT_TIMESTAMP获得的结果始终相同，而SYSDATE在中断先后则相差了2秒。版本
实际上，NOW和CURRENT_TIMESTAMP没有任何区别，他们都表示的是SQL开始执行时的系统时间；而SYSDATE则表示执行此函数时的系统时间。

字串时间戳转换int时间

replace(UNIX_TIMESTAMP(now(6)),'.','')

时间戳 字符串与数字互相转换


 date(from_unixtime(match_time))  

Other
MySQL日期 字符串 时间戳互转
平时比较常用的时间、字符串、时间戳之间的互相转换，虽然常用但是几乎每次使用时候都喜欢去搜索一下用法；本文将作为一个笔记，整理一下三者之间的 转换（即：date转字符串、date转时间戳、字符串转date、字符串转时间戳、时间戳转date，时间戳转字符串）用法，方便日后查看；
涉及的函数
date_format(date, format) 函数，MySQL日期格式化函数date_format()
unix_timestamp() 函数
str_to_date(str, format) 函数
from_unixtime(unix_timestamp, format) 函数，MySQL时间戳格式化函数from_unixtime
时间转字符串
[sql] 预览复制
select date_format(now(), '%Y-%m-%d');  
  
#结果：2016-01-05  
时间转时间戳
[sql] 预览复制
select unix_timestamp(now());  
  
#结果：1452001082  
字符串转时间
[sql] 预览复制
select str_to_date('2016-01-02', '%Y-%m-%d %H');  
  
#结果：2016-01-02 00:00:00  
字符串转时间戳
[sql] 预览复制
select unix_timestamp('2016-01-02');  
  
#结果：1451664000  
时间戳转时间
[sql] 预览复制
select from_unixtime(1451997924);  
  
#结果：2016-01-05 20:45:24  
时间戳转字符串
[sql] 预览复制
select from_unixtime(1451997924,'%Y-%d');  
  
//结果：2016-01-05 20:45:24  
附表
MySQL日期格式化（format）取值范围。


ref


MYSQL中NOW、CURRENT_TIMESTAMP、SYSDATE的区别 - 尚码园
