基与http url通用的查询rest接口



一般一个系统的80%是查询，20%是修改，
所以查询的通用rest接口很重要。可以大力提升扩展性以及简化工作量

在内部系统里面我们可以直接建立一个rest接口
/api?url=mysqlurl&sql= xxxx  来实现通用查询和修改。。 对外的接口不能直接暴露sql，会引起安全问题。。解决思路是受限的安全dsl（可以全面解析，过滤不安全的操作与资源）

首先是查询与修改相分离，查询相对可以应用更加宽松的安全机制。。 


通用查询实现的目标
可以自由组合选择要展示的字段
类似sql里面的select关键字功能。。

可以查询所有的库表与视图（默认）
黑名单机制可以禁止查询某些库表

支持多元化条件查询
支持多样化的排序支持orderby 支持翻页


支持join组合,支持groupby等统计功能
子查询组合支持,多查询支持（一次返回多个数据集合）
减少io往返。。多查询的实现一般是组合多个dsl语句，分号分割，一次发送。。后端接手后分别执行，最后组合成json array list返回

Pretty print支持（默认）
返回数据可以选择是否pretty格式化模式，提升可读性
支持数据库函数与自定义函数

通用查询实现原理
基本是吧sql各个部分关键词拆开映射到http url参数去。。或者json参数。
这样方便解析过滤安全性，以及方便应用各种黑白名单机制等。。然后组合为sql，扔到数据库去查询

Sql关键词映射表
http url与sql的关键词对应表



范例（rest风格）

简单查询 自定义返回字段集合
实现 select * from  db.table1的查询
/queryApi/db.table1            即可。。


Select a,b from db3.tab1
/queryApi/db3.tab1?_select=a,b


用户登录后查询自己的某些库表数据
/queryApi/db1.tab1?_select=a,b&b=1&userid=$uid
可以使用魔法变量$uid指示后端使用当前登录用户的id替换
后端会翻译为
Select a，b from db1.tab1 where b =1 and userid=22222

带数据库函数的查询
/queryApi/db1.tab1?_select=a&b=in(1,2,3)
Select a from db1.tab1 where b in(1,2,3)


翻页查询
实现select a,b  from db5.table1 where c=2 and d=3 order by e desc limit 10 

/queryApi/db5.table1 ?_select=a,b&c=2 & d=3 & _orderby=e desc&_page=1&_pagesize=10

实现join查询(不跨库与跨库均支持）
Select a.*,b.year,b.montd   from a join b on a.id=b.id

直接使用join语句替换表名位置即可
/queryApi/a join b on a.id=b.id?_select=a.*,b.year,b.montd
这里可能需要url编码，或者直接建立查询视图view1，在视图里面去join
就可以简化为/queryApi/db5.view1



分组查询groupby
/queryApi/db5.table1？_select=a,sum(b) as 总和&_groupby=a
相当于 select a,sum(b) as 总和 from db5.table1 group by a

复杂逻辑查询条件（or not查询），类似  where a=1 or b=3。。
参考es Elasticsearch 的rest接口json实现即可，这个相对使用较少

非rest风格
如果不想使用REST风格，表名可以使用_from字段放入即可
/queryApi.php?_select=a,b&_from=db1.tab3


一些安全机制
登录用户标识uid与魔法变量机制
大部分查询可能需要用户登录以后查询。。如果用户没有传递uid则可拒绝其查询业务表
可用登录后uid替换dsl里面的魔法变量$uid,$uname等
可设置默认查询条数1000条，防止过多消耗资源
字段内容过滤特殊符号，带函数的送入sql解析器安全解析
表名黑名单机制
少量的表包含一些敏感字段，不希望直接查询，可以加入黑名单限制即可。。比如user表包含密码字段。。可以建立一个安全视图  user_view，过滤掉敏感字段，查询此安全视图即可。。

安全视图机制

安全函数机制
可以设立一些函数黑名单，不予许执行一些函数。Mysql还好，基本没有shell函数，mssql 和oracle可能需要禁止一些shell类函数。。

Sql解析器安全解析过滤
可以使用sql解析器二次过滤检查

