Atitit hibernate面试题与答案


常见注解
@Entity表明实体类   	@Id表明主键字段

常见功能与api
Save（)  update() delete()  查询用sql hql等
一句话概括就是增删改查数据库

好处与优点
和其他orm框架比如mybatis 类似，把数据库操作独立出来 ，给程序的维护带来了很大便利  大大简化了Java数据库编程的重复工作
和mybatis的联系与区别
相同点，都是orm框架，做持久化
区别： mybatis更加简单，hb复杂些。
Mybatis只有sql api，，hb除了sql api，还有hql 和 oo api


Orm （mybatis/Hibernate ）中的Session指的是什么，和web中的session有何联系和区别？？

Hibernate/mybatis中的Session和web的session一样都是，存储会话信息。。
相当于jdbc中的conn。。
区别主要在其运行范围，一个是web层，一个是存储层orm层
 二级缓存指的是什么？ 
这个orm框架提供的缓存机制，和mybatis这一类orm框架类似，用来缓存数据，提升性能。


 Orm (hibernate mybatis) 实现一对多有几种方式,怎么操作的？ 

        有联合查询和嵌套查询,联合查询是几个表联合查询, 
        嵌套查询是先查一个表,根据这个表里面的 结果的外键id,去再另外一个表里面查询数据, 
可以通过配置对应的注解或xml来实现

动态sql
Hb里面直接使用java的流程控制if else for等
Mybatis里面可使用 动态sql的9个标签，trim|where|set|foreach|if|choose|when|otherwise|bind等


延迟加载？如果支持，它的实现原理是什

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。 
当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的


接口绑定配置有几种实现方式,分别是怎么实现的? 
        接口绑定有两种实现方式,一种是通过注解绑定 
        另外一种就是通过xml里面 
2、什么情况下用注解绑定,什么情况下用xml绑定？ 
        当比较简单时候,用注解绑定,不适合注解的情况下,可用xml绑定


 半自动ORM映射工具 与全自动的区别在哪里？
Mybatis是半自动ORM映射工具
Hibernate属于全自动ORM映射工具，使用Hibernate查询关联对象或者关联集合对象时，可以根据对象关系模型直接获取，所以它是全自动的。而Mybatis在查询关联对象或关联集合对象时，需要手动编写sql来完成，所以，称之为半自动ORM映射工具


