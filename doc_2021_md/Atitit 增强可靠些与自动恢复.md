Atitit 增强可靠些与自动恢复   

尽可能使用恢复模式代替exit 模式

Try catch

数据库死锁问题
使用菲阻塞锁，，设置lock wait =1
设置query timeout=7s




queryInterceptors

逗号分隔的类列表，这些类实现“ com.mysql.cj.interceptors.QueryInterceptor”，应将其放置在查询执行之间以影响结果。QueryInterceptor是“可链接的”，“当前”拦截器返回的结果将按照此属性的指定从左到右顺序传递到链中的下一个。



queryTimeoutKillsConnection

如果Statement.setQueryTimeout（）中给出的超时到期，驱动程序是否应该强制中止Connection而不是尝试中止查询？


zeroDateTimeBehavior
当驱动程序遇到完全由零组成的DATETIME值（由MySQL用来表示无效日期）时，应该怎么办？有效值为“ EXCEPTION”，“ ROUND”和“ CONVERT_TO_NULL”。
enableQueryTimeouts
启用后，通过Statement.setQueryTimeout（）设置的查询超时将使用共享的java.util.Timer实例进行调度。即使超时没有在查询处理之前到期，TimerTask仍将使用给定超时的内存，直到超时没有到期时，驱动程序才将其取消，直到该超时被驱动程序取消为止。高负载环境可能要考虑禁用此功能。

includeInnodbStatusInDeadlockExceptions

当检测到死锁异常时，在异常消息中包括“ SHOW ENGINE INNODB STATUS”的输出？



includeThreadDumpInDeadlockExceptions

当检测到死锁异常时，在异常消息中包括当前的Java线程转储？



includeThreadNamesAsStatementComment

将当前线程的名称作为注释显示在“ SHOW PROCESSLIST”或Innodb死锁转储中，这与“ includeInnodbStatusInDeadlockExceptions = true”和“ includeThreadDumpInDeadlockExceptions = true”相关。



