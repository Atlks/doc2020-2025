Atitit impt db core table create数据库建表流程


创建表user
 CREATE TABLE user (
    id int(11) NOT NULL AUTO_INCREMENT,
    name varchar(10) DEFAULT NULL,
    age int(11) DEFAULT NULL,
    gender smallint(6) DEFAULT NULL,
    create_time date DEFAULT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4复制代码
innodb向系统表空间的information_schema库的tables和columns中存入表结构信息

创建表空间 同时创建独立表空间world/user以及对应的数据文件world/user.ibd，并更新到information_schema.innodb_tablespaces中 
同步更新表空间所对应的文件信息到information_schema.files中 
规定表空间0号文件即world/user.ibd文件的0号页为表空间的封面页。
创建聚集索引 如果指定的主键或唯一索引，则使用指定的列创建聚集索引，否则使用隐藏列row_id创建聚集索引，并存储到information_schema.innodb_indexes中 
为索引创建两个段：索引段（非叶子节点）和数据段（叶子节点），并把段信息存储到表空间封面页的段链表中。
为索引创建第一页即Root Page，把段信息记录在Root Page的段链表中，从而管理本B+树的段信息。同时把Root PageNo记录到information_schema.innodb_indexes中，如上图。从页使逻辑表与物理存储关联起来，这个Root Page相当于索引的封面。

作者：敖丙
链接：https://juejin.cn/post/6919263740122628109
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。


