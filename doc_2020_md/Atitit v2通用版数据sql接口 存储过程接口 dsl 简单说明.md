Atitit v2通用版数据sql接口 存储过程接口 dsl 简单说明


1.1. 查询数据范例	1
1.2. 新增与更新数据接口	2
2. 常用的sql语句	3
2.1. 查询 select * from l_notice	3
2.2. 获取翻页记录总数 使用count函数	3
2.3. 条件查询 select * from l_notice where member_no=20120216	3
2.4. 增加数据 insert l_notice(content)values('tttt')	3
2.5. 更新数据  使用sql update	4
3. Sql的安全性增强	4

查询数据范例
http://localhost:8080/AjaxJsbridge_HttpparamMode_servlet?m=com.attilax.db.DbServiceV4qb9.executeQuery&p1=select+*+from+s_member+limit+10&iocFac=com.attilax.ioc.Ioc4wash

返回json列表数据

参数说明
m:就是查询sql的方法，位com.attilax.db.DbServiceV4qb9.executeQuery
P1:就是 具体的查询数据sql 
iocFac： 就是ioc工厂，在洗衣项目为com.attilax.ioc.Ioc4wash


新增与更新数据接口
http://localhost:8080/AjaxJsbridge_HttpparamMode_servlet?m=com.attilax.db.DbServiceV4qb9.executeUpdate&p1=insert+l_notice%28content%29values%28%27tttt%27%29&iocFac=com.attilax.ioc.Ioc4wash&retFmt=none


返回一个数字，表面受影响的行数

作者 attilax ail   q1466519819


常用的sql语句
查询 select * from l_notice
获取翻页记录总数 使用count函数

条件查询 select * from l_notice where member_no=20120216
返回结果



增加数据 insert l_notice(content)values('tttt')  
返回一个数字，表示增加了多少行，一般为1


更新数据  使用sql update

Sql的安全性增强
需要吧他存到sp存储过程里面去，目前为了快速测试，可以先放在前面。




