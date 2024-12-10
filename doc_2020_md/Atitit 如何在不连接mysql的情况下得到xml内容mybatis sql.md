Atitit 如何在不连接mysql的情况下得到xml内容mybatis sql

修改mysql驱动，获取到一个factory这样就可以继续mybatis了。。

然后执行selectLsit，，通过拦截器，得到具体sql



从以下代码可以看出mybatis 在实例化Executor、ParameterHandler、ResultSetHandler、StatementHandler四大接口对象的时候调用interceptorChain.pluginAll() 方法插入进去的。其实就是循环执行拦截器链所有的拦截器的plugin() 方法，
mybatis官方推荐的plugin方法是Plugin.wrap() 方法,这个类就是我们上面的TargetProxy类
————————————————
版权声明：本文为CSDN博主「M义薄云天」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_39494923/article/details/91534658

Mybatis源码分析一：一条sql语句如何被执行 - - SegmentFault 思否.html
Atitit 自定义mysql驱动 方便测试获取mybatis sql
Atitit mybatis拦截器机制

