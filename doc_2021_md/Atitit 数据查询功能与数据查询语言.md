Atitit 数据查询功能与数据查询语言（DQL）

数据查询语言（DQL）

一、 数据查询语言(DQL)(重中之重)

完整语法格式：

select 表达式1|字段,....
[from 表名 where 条件]
[group by 列名]
[having 条件]
[order by 列名 [asc|desc]]
[limit 位置,数量]



<1> 普通查询  select 查询表达式; 

select 查询表达式;  // 最简单的sql语句，是一个函数
select database();
select version();
select now();

<2> 条件查询

where 条件表达式, 支持运算符和函数
MySQL支持的运算符：

=、 !=、 >、 >=、 <、 <=、 <>
and、 or、 not
is null、 is not null
between...and... （区间查询，多少到多少之间）
in(set);
like 通配符和占位符: % _ （模糊查询）

%: 表示0个或者多个字符
_: 表示占位一个





-- 查询所有的老师信息
	select * from teacher;

-- 查询id 大于2的老师信息
	select * from teacher where id>2;
 
-- 查询姓名为空的老师信息    在数据库中null永远都不等于null，那么怎么去判断null值？通过 is null / is not null
-- select * from teacher where name=null; # 错误
	select * from teacher where name is not null;

-- 查询id为1 并且 姓名是 "xiaosi"的老师信息
	select * from teacher where id=1 and name='xiaosi';

-- 查询id为1 并且 姓名是 "xiaosi"的老师信息
	select * from teacher where id=1 or name='xiaosi';

-- 查询薪水在2000到10000之间的老师信息
	select * from teacher where sal >=2000 and sal <=10000;
	select * from teacher where sal between 2000 and 10000; # 这种方式等同于上面

-- 查询姓名中有 ‘尘’ 字的老师信息
	select * from teacher where name like '%尘%';

-- 查询姓名是三个字的
	select * from teacher where name like '___';

-- 查询姓 '小' 的老师信息
	select * from teacher where name like '小%';

-- 查询名字中含有下划线的老师信息  '\' 转义
-- select * from teacher where name like '%_%';  # 错误
	select * from teacher where name like '%\_%';  
复制代码
<4> 排序查询

语法格式：

order by 列名 asc|desc 默认升序(asc)



-- 查询老师信息，根据薪资进行排序，要求从大到小进行排序
select * from teacher order by sal desc;  # 根据sal进行降序排序
select * from teacher order by sal asc;  # 根据sal进行升序排序
select * from teacher order by sal;  # 根据sal进行升序排序, 利用默认排序
复制代码
<5> 限制结果集数量的查询(分页)
编号    商品名称    商品价格    操作
1         玩具娃娃    100.0         删除 修改
2         玩具汽车    200.0         删除 修改
3         玩具飞机    300.0         删除 修改
................................
首页    上一页    1 2 3 4 5    下一页   尾页

语法格式

limit n条数;-------从第一条开始取n条数据(了解)
limit start开始下标索引，count条数; ---- 从起始位置start取count条数据(起始位置是从0开始的)  （推荐使用）



分页(每页显示两条数据)
第一页：select * from teacher limit 0,2;
第二页：select * from teacher limit 2,2;
第三页：select * from teacher limit 4,2;
第四页：select * from teacher limit 6,2;
第五页：select * from teacher limit 8,2;
复制代码

分页公式:

开始下标索引(起始位置) = (当前页-1)*每页显示条数;



-- 每页显示3条
-- 显示第二页
	select * from teacher limit 3,3;
复制代码


<3> 分组查询

语法格式：

[group by 列名] [haveing 条件]
一般情况分组查询结合聚合函数一起使用

max()
min()
sum()
avg()
count()





-- 查询每个部门的平居薪资
	# select * from teacher GROUP BY dname
	# 记住：分组的正确使用方式，group by 后面没有出现的列名不能出现在select 和from 的中间，
  # 虽然不报错，但是不是分组的正确使用方式
	# 聚合函数中出现的列名group by后面没有无所谓
	select dname from teacher GROUP BY dname;
	select dname, avg(sal) from teacher GROUP BY dname;
复制代码

<6> 扩展  别名机制等

别名

select * from teacher;  # 查询表中所有字段记录

select name, sal, dname from teacher;  # 查询表中指定字段记录

-- 给查询的字段设置别名  同时也可以给表设置别名  通过as 关键字实现别名
	select name as '姓名', sal '薪资', dname '部门名称' from teacher 

作者：ruochen
链接：https://juejin.cn/post/6927099020330893319
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
