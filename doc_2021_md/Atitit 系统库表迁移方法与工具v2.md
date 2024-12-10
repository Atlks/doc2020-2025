Atitit 系统库表迁移方法与工具

单表迁移
不必改写sql ，增加视图匹配即可。。。可以insert ，select 视图
改写sql，改变sql即可。。为 db.tabname..


多个分表如何单个个迁移到另外一个库

使用视图改变引用。。迁移一个改变一个视图即可。。

View=  sp.tab1  
View2=sp.tab2

