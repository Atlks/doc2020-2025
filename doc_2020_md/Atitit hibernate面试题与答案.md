Atitit hibernate面试题与答案


常见注解
@Entity表明实体类   	@Id表明主键字段

常见功能与api
Save（)  update() delete()  查询用sql hql等
一句话概括就是增删改查数据库

和mybatis的联系与区别
相同点，都是orm框架，做持久化
区别： mybatis更加简单，hb复杂些。
Mybatis只有sql api，，hb除了sql api，还有hql 和 映射api


Hibernate中的Session指的是什么，和web中的session有何联系和区别？？

Hibernate中的Session和web的session一样都是，存储会话信息。。相当于jdbc中的conn。。
区别主要在其运行范围，一个是web层，一个是存储层orm层
Hibernate中二级缓存指的是什么？ 这是同Hibernate的缓存机制相关的第一个面试问题
这个orm框架提供的缓存机制，和mybatis这一类orm框架类似，用来缓存数据，提升性能。

