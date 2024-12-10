Mybatis面试题
一、什么是mybatis？
MyBatis是支持普通SQL查询,存储过程和高级映射的优秀持久层框架.MyBatis封装了几乎所有的JDBC代码和参数的手工设置以及结果集的检索;使用简单的XML或注解做配置和定义映射关系，比 Hibernate 灵活，但移植性差。

二、mybatis中的#和$的区别
http://www.cnblogs.com/kangyun/p/5881531.html
#{}的解析发生在dbms（关系型数据库）中，在java中参数使用？占位，在dbms中处理参数，能够很大程度防止sql注入
${}的解析发生在java中，直接在Java程序中进行简单的字符串替换，容易导致sql注入。${}一般用于传输数据库的表名、字段名等
所以尽量使用#{}

三、MyBatis的技术特点、优点
http://blog.csdn.net/wangpeng047/article/details/17039573
优点：
1. 易于上手和掌握。
2. sql写在xml里，便于统一管理和优化。
3. 解除sql与程序代码的耦合。
4. 提供映射标签，支持对象与数据库的orm字段关系映射
5. 提供对象关系映射标签，支持对象关系组建维护
6. 提供xml标签，支持编写动态sql。
缺点：
1）编写sql工作量大
2）不易于数据库移植
3）查询出结果集后，如果列名和属性不匹配，必须手工组装
4） 编写动态sql时,不方便调试，尤其逻辑复杂时。
5） 若不查询主键字段，容易造成查询出的对象有“覆盖”现象。
6） 缓存使用不当，容易产生脏数据。

四、MyBatis的三层架构
1、基础支撑层：负责读取mybatis配置文件，链接数据库，做事物管理
2、数据处理层：解析sql、执行sql、映射结果集
3、API接口层：提供操作数据的api

五、mybatis传递多参数
map形式、注解形式、索引形式

六、mybatis映射文件中遍历list用什么标签
<foreach>

七、Mybatis动态sql是做什么的？都有哪些动态sql？能简述一下动态sql的执行原理不？

八、mybatis动态sql中的trim标签的使用 

九、MyBatis的常用配置
常见的配置项有：配置pojo的别名、配置映射文件的位置、配置 sqlSessionFactory、在Mapper扫描器中配置dao接口

十、mybatis的批量插入	
<foreach>
主要偏向于数据库压力测试

十一、Mybatis运行原理

文字解释MyBatis运行原理

把配置文件流交由XMLConfigBuilder进行解析,解析后把所有配置信息封装到了Configuration中,在把Configuration传递给DefaultSqlSessionFactory,并实例化这个类.
源码可以看出DefaultSqlSessionFactory是SqlSessionFactory的实现类,所以这个时候就产生了SqlSessionFactory接口的实例.
需要openSession,产生SqlSession示例,根据SqlSession实例执行事务.最后要提交事务和关闭SqlSession
通常都不关闭SqlSessionFactory,在大点的项目中,都需要用到二级缓存,所以不关闭.

十二、模糊查询like语句该怎么写?


十三、列举MyBatis的常用API及方法


十四、简述MyBatis的体系结构


十五、JDBC编程有哪些不足之处，MyBatis是如何解决这些问题的？


十六、Mybatis是如何进行分页的？分页插件的原理是什么？


十七、Xml映射文件中，除了常见的select|insert|updae|delete标签之外，还有哪些标签？


十八、最佳实践中，通常一个Xml映射文件，都会写一个Dao接口与之对应，请问，这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗？


十九、简述Mybatis的插件运行原理，以及如何编写一个插件。


二十、为什么说Mybatis是半自动ORM映射工具？它与全自动的区别在哪里？


二十一、mybatis的缓存[一级缓存、二级缓存]


二十二、Mybatis比IBatis比较大的几个改进是什么


二十三、什么情况下用注解绑定,什么情况下用xml绑定

二十四、如何配置二级缓存

二十五、什么样的数据适合存放到第二级缓存中？ 
1) 很少被修改的数据 　　
2) 不是很重要的数据，允许出现偶尔并发的数据 　　
3) 常量数据 　
不适合存放到第二级缓存的数据？ 
1) 经常被修改的数据 　　
2) 绝对不允许出现并发访问的数据，如财务数据，绝对不允许出现并发 　　	 3) 与其他应用共享的数据。

二十六、jdbc,mybatis,hibernate的区别


二十七、mybatis延迟加载
即懒加载，在关联查询时，利用延迟加载，先加载主信息。需要关联信息时再去按需加载关联信息。这样会大大提高数据库性能，因为查询单表要比关联查询多张表速度要快。
二十八、延迟加载的实例
如果查询订单并且关联查询用户信息。如果先查询订单信息即可满足要求，当我们需要查询用户信息时再查询用户信息。把对用户信息的按需去查询就是延迟加载。
二十九、如何开启延迟加载功能

三十一、延迟加载它的实现原理是什么？

三十三、Mybatis的Xml映射文件中，不同的Xml映射文件，id是否可以重复？

答：不同的Xml映射文件，如果配置了namespace，那么id可以重复；如果没有配置namespace，那么id不能重复；毕竟namespace不是必须的，只是最佳实践而已。
原因就是namespace+id是作为Map<String, MappedStatement>的key使用的，如果没有namespace，就剩下id，那么，id重复会导致数据互相覆盖。有了namespace，自然id就可以重复，namespace不同，namespace+id自然也就不同。
三十四、Mybatis中如何执行批处理？
答：使用BatchExecutor完成批处理。

三十五、Mybatis都有哪些Executor执行器？它们之间的区别是什么？
答：Mybatis有三种基本的Executor执行器，SimpleExecutor、ReuseExecutor、BatchExecutor。
SimpleExecutor：每执行一次update或select，就开启一个Statement对象，用完立刻关闭Statement对象。
ReuseExecutor：执行update或select，以sql作为key查找Statement对象，存在就使用，不存在就创建，用完后，不关闭Statement对象，而是放置于Map<String, Statement>内，供下一次使用。简言之，就是重复使用Statement对象。
BatchExecutor：执行update（没有select，JDBC批处理不支持select），将所有sql都添加到批处理中（addBatch()），等待统一执行（executeBatch()），它缓存了多个Statement对象，每个Statement对象都是addBatch()完毕后，等待逐一执行executeBatch()批处理。与JDBC批处理相同。
作用范围：Executor的这些特点，都严格限制在SqlSession生命周期范围内。

三十六、Mybatis中如何指定使用哪一种Executor执行器？
答：在Mybatis配置文件中，可以指定默认的ExecutorType执行器类型，也可以手动给DefaultSqlSessionFactory的创建SqlSession的方法传递ExecutorType类型参数。

三十七、Mybatis是否可以映射Enum枚举类？
答：Mybatis可以映射枚举类，不单可以映射枚举类，Mybatis可以映射任何对象到表的一列上。映射方式为自定义一个TypeHandler，实现TypeHandler的setParameter()和getResult()接口方法。TypeHandler有两个作用，一是完成从javaType至jdbcType的转换，二是完成jdbcType至javaType的转换，体现为setParameter()和getResult()两个方法，分别代表设置sql问号占位符参数和获取列查询结果。

三十八、简述Mybatis的Xml映射文件和Mybatis内部数据结构之间的映射关系？
答：Mybatis将所有Xml配置信息都封装到All-In-One重量级对象Configuration内部。在Xml映射文件中，<parameterMap>标签会被解析为ParameterMap对象，其每个子元素会被解析为ParameterMapping对象。<resultMap>标签会被解析为ResultMap对象，其每个子元素会被解析为ResultMapping对象。每一个<select>、<insert>、<update>、<delete>标签均会被解析为MappedStatement对象，标签内的sql会被解析为BoundSql对象。

三十九、Mybatis映射文件中，如果A标签通过include引用了B标签的内容，请问，B标签能否定义在A标签的后面，还是说必须定义在A标签的前面？
答：虽然Mybatis解析Xml映射文件是按照顺序解析的，但是，被引用的B标签依然可以定义在任何地方，Mybatis都可以正确识别。
原理是，Mybatis解析A标签，发现A标签引用了B标签，但是B标签尚未解析到，尚不存在，此时，Mybatis会将A标签标记为未解析状态，然后继续解析余下的标签，包含B标签，待所有标签解析完毕，Mybatis会重新解析那些被标记为未解析的标签，此时再解析A标签时，B标签已经存在，A标签也就可以正常解析完成了。
