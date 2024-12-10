Atitit dbms 现代数据库的功能


现代的DBMS通常提供以下所有功能，而MapReduce则全部缺少这些功能：
批量加载器-将文件中的输入数据转换为所需格式并将其加载到DBMS中
索引-如上所述
更新-更改数据库中的数据
事务-支持并行更新以及从更新期间的故障中恢复
完整性约束-帮助将垃圾排除在数据库之外
参照完整性-再次帮助将垃圾排除在数据库之外
视图-这样架构就可以更改而不必重写应用程序

总之，MapReduce仅提供了现代DBMS中的一小部分功能。


5. MapReduce与DBMS工具不兼容

现代SQL DBMS具有以下所有类别的工具：
报表编写器（例如，Crystal报表）为人类可视化准备报表
商业智能工具（例如，Business Objects或Cognos），可以对大型数据仓库进行即席查询
数据挖掘工具（例如Oracle Data Mining或IBM DB2 Intelligent Miner）允许用户发现大型数据集中的结构
复制工具（例如，Golden Gate）允许用户将数据从DBMS上复制到另一个
数据库设计工具（例如，Embarcadero）可帮助用户构建数据库。


