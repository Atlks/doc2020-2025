Atitit v3通用版数据sql接口 存储过程接口 dsl 简单说明


1.1. 查询数据范例	1
1.2. 新增与更新与删除数据接口	2
1.3. 删除数据接口	3
2. 常用的sql语句	3
2.1. 查询 select * from l_notice	3
2.2. 获取翻页记录总数 使用count函数	3
2.3. 条件查询 select * from l_notice where member_no=20120216	4
2.4. 增加数据 insert l_notice(content)values('tttt')	4
2.5. 更新数据  使用sql update	4
2.6. 删除数据	4
3. Sql的安全性增强	4


版本历史
V2 完善了文档，增加了删除等
V3 增加了简化版接口。。
返回值类型自动判断，基本类型直接返回。。否则序列号为json返回
查询数据范例

简化版接口
http://localhost:8080/api?m=q&p1=select+*+from+s_member+limit+10


原版接口
http://localhost:8080/AjaxJsbridge_HttpparamMode_servlet?m=com.attilax.db.DbServiceV4qb9.executeQuery&p1=select+*+from+s_member+limit+10&iocFac=com.attilax.ioc.Ioc4wash

返回json列表数据

参数说明
m:就是查询sql的方法，位com.attilax.db.DbServiceV4qb9.executeQuery
,,q指的就是query ，u指的update
,p1:就是 具体的查询数据sql 
iocFac： 就是ioc工厂，在洗衣项目为com.attilax.ioc.Ioc4wash


新增与更新与删除数据接口

简化版接口
http://localhost:8080/api?m=u&p1=insert+l_notice%28content%29values%28%27tttt%27%29


http://localhost:8080/AjaxJsbridge_HttpparamMode_servlet?m=com.attilax.db.DbServiceV4qb9.executeUpdate&p1=insert+l_notice%28content%29values%28%27tttt%27%29&iocFac=com.attilax.ioc.Ioc4wash&retFmt=none


返回一个数字，表面受影响的行数

作者 attilax ail   q1466519819

删除数据接口
基本与更新接口一直，只有那个p1参数不同要换成删除数据的sql语句。

http://localhost:8080/AjaxJsbridge_HttpparamMode_servlet?iocFac=com.attilax.ioc.Ioc4wash&m=com.attilax.db.DbServiceV4qb9.executeUpdate&retFmt=none&p1=delete from `常用洗衣网点` where id=1

注意p1参数需要urlencode。。这里为了显示方便，没有encode


常用的sql语句
查询 select * from l_notice
获取翻页记录总数 使用count函数

条件查询 select * from l_notice where member_no=20120216
返回结果



增加数据 insert l_notice(content)values('tttt')  
返回一个数字，表示增加了多少行，一般为1


更新数据  使用sql update
删除数据
删除数据的sql 

 delete from `常用洗衣网点` where id=1
Sql的安全性增强
需要吧他存到sp存储过程里面去，目前为了快速测试，可以先放在前面。






