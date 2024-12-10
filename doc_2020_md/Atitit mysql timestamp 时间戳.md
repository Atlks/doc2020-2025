Atitit mysql timestamp 时间戳

函数now  别名
和current_timestamp 一个含义。。。
current_timestamp不带括号只能用在默认只里面
SYSDATE
Now 是字符串模式
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


MYSQL中NOW、CURRENT_TIMESTAMP、SYSDATE的区别 - 尚码园
