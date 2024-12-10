Atitit 数据库 提升稳定性 策略


死锁和死锁检测
当并发系统中不同线程出现循环资源依赖，涉及的线程都在等待别的线程释放资源时，就会导致这几个线程都进入无线等待的状态，称为死锁。


当出现死锁以后，有两种策略：
1. 一种策略是，直接进入等待，知道超时。这个超时时间可以通过参数 innodb_lock_wait_timeout 来设置。
另一种策略是，发起死锁检测，发现死锁后，主动回滚死锁链条中的某一个事务，让其他事务得以继续执行。将参数 innodb_deadlock_detect 设置为 on，表示开启这个逻辑。


innodb_print_all_deadlocks 死锁日志开启

断线重连url 参数 autoReconnect
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/test?allowMultiQueries=true&autoReconnect=true
jdbc.username=root
jdbc.password=
