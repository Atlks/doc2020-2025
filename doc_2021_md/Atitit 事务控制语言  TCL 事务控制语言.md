Atitit 事务控制语言  TCL 事务控制语言


TCL 事务控制语言_创造未来-CSDN博客blog.csdn.net › gongxiude › article › details
2013年11月15日 — TCL 事务控制语句什么是事务:用于确保数据的一致性,由一组相关的DML组成, 该组DML的操作要么全确认,要么全取消比如银行转账业务步骤


手动关闭事务提交语法：

set autocommit = false|true;  // 设置事务的提交方式
rollback;  // 事务回滚
commit;  // 事务提交
savepoint 节点名称;  // 设置回滚的节点
rollback to 节点名称;  // 回滚到具体的某个节点



set autocommit = false;  # 设置事务手动提交

select * from student;

delete from student where id=1;  # 删除id为1 的信息

rollback;  # 事务回滚
commit;  # 事务提交

update student set money = money-30000 where id=1;
savepoint t1;  # 设置事务节点
update student set money = money-20000 where id=1;

rollback to t1;  # 回滚到t1节点位置
commit;  # 事务提交

作者：ruochen
链接：https://juejin.cn/post/6927099020330893319
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
