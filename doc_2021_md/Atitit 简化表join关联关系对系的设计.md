Atitit 简化表join关联关系对系的设计

User role的关联
冗余字段模式，使用逗号分隔，建立全文索引查询即可反向查询。。。。。。
里面内容必须是小表。。。学生选课。可以在user表增加选课id即可,格式
可以使用json模式    多个jo对象。。   12:数学，13：语文。。。

要获取雪休了语文对学生，反向全文索引即可 倒排索引



多对多关系的简化


