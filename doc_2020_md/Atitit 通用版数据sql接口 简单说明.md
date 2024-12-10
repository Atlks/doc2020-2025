Atitit 通用版数据sql接口 简单说明

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





