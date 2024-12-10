Atitit 提升mysql 稳定性和死锁优化


配置事务超时时间wait_timeout

查询事务列表 INNODB_TRX
# query trx
SELECT * FROM information_schema.INNODB_TRX;
kill 12; SELECT * FROM information_schema.INNODB_TRX;
update user set stat=9 ;
select * from  user;

 show global variables like '%timeout%';
set global lock_wait_timeout = 30; --
set global  deadlock_timeout_long=30;
set global  deadlock_timeout_short=30;
set global  wait_timeout=30;   #trans exe time out
set global  interactive_timeout=30;
set global  innodb_lock_wait_timeout=30;




MySQL 各种超时参数的含义 - xiaoboluo768 - 博客园

b)、interactive_timeout和wait_timeout：在连接空闲阶段（sleep）起作用

即使没有网络问题，也不能允许客户端一直占用连接。对于保持sleep状态超过了wait_timeout（或interactive_timeout，取决于client_interactive标志）的客户端，MySQL会主动断开连接。


官方描述：


wait_timeout：


