Atitit mybatis 3 3.2 3.3  3.4 新特性attilax总结

1.1. iBATIS 3 内的新特性.html	1
1.2. MyBatis团队于2013年2月21日正式发布 MyBatis 3.2.0	1
1.3. MyBatis 3.3.0 发布，此版本主要有两个改进：	1
1.4. 持久层框架 MyBatis v3.4.1 发布 2016-06-26 	2
2. Mybatis直接执行sql的改进 SqlMapper	2
2.1. SqlMapper提供的方法	2
3. 参考资料	5

iBATIS 3 内的新特性.html
随着开发团队转投Google Code旗下，ibatis3.x正式更名为Mybatis 
MyBatis团队于2013年2月21日正式发布 MyBatis 3.2.0
新特性包括:
支持可扩展脚本引擎
支持可扩展字节码提供器和Java辅助类
缓存嵌套查询
改善日志
修正了40余处BUG

MyBatis 3.3.0 发布，此版本主要有两个改进：

Ognl 升级至最新版本 3.0.11 


默认代理工具是 Javassist，放置在 mybatis jar 内


持久层框架 MyBatis v3.4.1 发布 2016-06-26 
更新日志
改进
Allow referencing parameters by their declared names when compiled with Java 8 -parametersoption. #549
Added auto-detection of Year/MonthTypeHandler added in mybatis-typehandlers-jsr310 1.0.1. #646
@Select can now return an array of objects. #669
Allow specifying custom reflectorFactory in XML config. #657

Mybatis直接执行sql的改进 SqlMapper
为了让通用Mapper更彻底的支持多表操作以及更灵活的操作，在2.2.0版本增加了一个可以直接执行SQL的新类SqlMapper。
通过这篇博客，我们来了解一下SqlMapper。
SqlMapper提供的方法
SqlMapper提供了以下这些公共方法：

Map<String,Object> selectOne(String sql)


Map<String,Object> selectOne(String sql, Object value)


<T> T selectOne(String sql, Class<T> resultType)


<T> T selectOne(String sql, Object value, Class<T> resultType)


List<Map<String,Object>> selectList(String sql)


List<Map<String,Object>> selectList(String sql, Object value)


<T> List<T> selectList(String sql, Class<T> resultType)


<T> List<T> selectList(String sql, Object value, Class<T> resultType)


int insert(String sql)


int insert(String sql, Object value)


int update(String sql)


int update(String sql, Object value)


int delete(String sql)


int delete(String sql, Object value)

//查询，返回List<Map> List<Map<String, Object>> list = sqlMapper.selectList("select * from country where id < 11")
//insert int result = sqlMapper.insert("insert into country values(1921,'天朝','TC')"); 
//update result = sqlMapper.update("update country set countryname = '天朝' where id = 35"); 
//delete result = sqlMapper.delete("delete from country where id = 35");

参考资料

持久层框架 MyBatis v3.4.1 发布 - OPEN资讯.html
MyBatis 3.3.0 发布，Ognl 升级至版本 3.0.11 - 开源中国社区.html
ibatis2.x与mybatis(ibatis3.x)的比较 - 赵先生不知何许人也的日志 - 网易博客.html
MyBatis直接执行SQL的工具SqlMapper - 偶尔记一下 - 博客频道 - CSDN.NET.html
