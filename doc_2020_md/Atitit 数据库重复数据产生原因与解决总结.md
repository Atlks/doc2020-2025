Atitit 数据库重复数据产生原因与解决总结


原因

缺少数据约束校验
表关系关联设计错误
导致left join多条对应
约束种类
非空约束(not null)
唯一性约束(unique)
主键约束(primary key) PK
外键约束(foreign key) FK
检查约束(目前MySQL不支持、Oracle支持)
分类 表级约束vs列级别约束
多列一般啊属于表级约束
外键约束(foreign key)FK只能是表级定义

Other
联合约束 可以使用unique实现
-> unique(name,email)
联合约束，表示两个或以上的字段同时与另一条记录相等，则报错
表级约束，给多个字段联合约束

解决法总结

增加主键，外键
增加unique索引
Trigger约束 实现检查约束
建议trigger仅仅trig，主体检查放入sp udf 方便测试。。
关联limit1
放弃表join，使用select字段udf join模式
