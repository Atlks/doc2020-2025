Atitit mybatis 翻页解决法

翻页模式还有js翻页前端翻页更加简单
逻辑分页使用类RowBounds  vs   物理分页 offset模式
Mybatis提供了一个简单的逻辑分页使用类RowBounds（物理分页当然就是我们在sql语句中指定limit和offset值），在DefaultSqlSession提供的某些查询接口中我们可以看到RowBounds是作为参数用来进行分页的，如下接口：

 

 public <E> List<E> selectList(String statement, Object parameter, RowBounds rowBounds)
--------------------- 
逻辑分页的实现原理：
 
在DefaultResultSetHandler中，逻辑分页会将所有的结果都查询到，然后根据RowBounds中提供的offset和limit值来获取最后的结果，DefaultResultSetHandler实现如下：
总结：Mybatis的逻辑分页比较简单，简单来说就是取出所有满足条件的数据，然后舍弃掉前面offset条数据，然后再取剩下的数据的limit条


Atitit mybatis翻页pagehelper 物理分页法

目录
1.1. ①.导入依赖	1
1.2. ②.在全局配置文件中配置插件	1
1.3. 翻页代码	2
1.4. PageInfo的方法	4
