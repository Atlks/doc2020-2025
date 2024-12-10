Atitit select insert update 语句的加锁机制


我们发现除了一个 IX 的 TABLE LOCK 之外，就没有其他的锁了，难道 INSERT 不加锁？一般来说，加锁都是对表中已有的记录进行加锁，而 INSERT 语句是插入一条新的纪录，这条记录表中本来就没有，那是不是就不需要加锁了？显然不是，至少有两个原因可以说明 INSERT 加了锁：

为了防止幻读，如果记录之间加有 GAP 锁，此时不能 INSERT；
如果 INSERT 的记录和已有记录造成唯一键冲突，此时不能 INSERT；

