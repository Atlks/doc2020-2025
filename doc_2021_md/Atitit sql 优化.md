Atitit sql 优化，需要强制制定索引的情况


7.如果在 where 子句中使用参数，也会导致全表扫描。因为 SQL 只有在运行时才会解析局部变量，但优 化程序不能将访问计划的选择推迟到运行时;它必须在编译时进行选择。然 而，如果在编译时建立访问计 划，变量的值还是未知的，因而无法作为索引选择的输入项。如下面语句将进行全表扫描：
Sql 代码 : select id from t where num=@num ;
可以改为强制查询使用索引：
Sql 代码 : select id from t with(index(索引名)) where num=@num ;

