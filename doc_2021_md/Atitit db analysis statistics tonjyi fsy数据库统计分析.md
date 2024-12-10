Atitit db analysis statistics tonjyi fsy数据库统计分析
Atitit 数据库表与注释文档与统计（表，说明）


 
目录
1.1. 6600多个表  包含所有的全局元数据表 和日志类业务表	1
1.2. 元数据类表191个表（表数据增长缓慢，没有分表）	1
1.3. 日志类业务表（实际为34个逻辑总表，物理六千多个表）	6

获取表列表 数据库包含哪些表。视图等。。


select * from INFORMATION_SCHEMA.TABLES where table_schema='laundry'

select table_schema 数据库,table_name 表名,table_type 类型,table_comment 注释 from INFORMATION_SCHEMA.TABLES where table_schema='laundry'


统计元表与业务日志表
使用正则表达式  元表没有数字结尾

分别统计业务表，8位数字结尾。。。并distinct
表结构文档（表，表注释，字段，字段注释）

SELECT
	c.table_schema 数据库,
	c.table_name  ,table_comment,
	c.column_name 列名,
 
	column_comment  注释含义
FROM
	information_schema. COLUMNS c left join  INFORMATION_SCHEMA.TABLES t on t.table_name=c.table_name 
WHERE
	c.table_name in( 'ssc_play_pl_group','ssc_play_pl_company','ssc_play_pl')
ORDER BY
	c.table_schema,
	c.table_name

Atitit 数据库表文档生成解决方案

1.1. Sql dml文件结构法 最快速	1
1.2. Sql法+sp存储过程 （表格式样）	1
1.3. Navicate uml法 （uml格式）	2
1.4. H5 报表法图表法（可视化好看与实用性结合）	2
1.5. Meta api法	3
1.6. 获取表列表 数据库包含哪些表。视图等。。	3


体积与行数统计（数据，索引体积，行数）
数据索引总体积
select (sum(`统计表体积与行数`.`totalSize_Mb`) / 1024) AS `size_sum_GB` from `cp`.`统计表体积与行数`

每个表对数据索引体积

 select `information_schema`.`tables`.`TABLE_NAME` AS `TABLE_NAME`,`information_schema`.`tables`.`DATA_LENGTH` AS `DATA_LENGTH`,`information_schema`.`tables`.`INDEX_LENGTH` AS `INDEX_LENGTH`,((`information_schema`.`tables`.`DATA_LENGTH` + `information_schema`.`tables`.`INDEX_LENGTH`) / 1000000) AS `totalSize_Mb`,(`information_schema`.`tables`.`DATA_LENGTH` / `information_schema`.`tables`.`INDEX_LENGTH`) AS `数据索引体积比`,`information_schema`.`tables`.`TABLE_ROWS` AS `TABLE_ROWS` from `information_schema`.`tables` where ((`information_schema`.`tables`.`TABLE_SCHEMA` = 'cp') and (`information_schema`.`tables`.`TABLE_ROWS` > 500)) order by `information_schema`.`tables`.`TABLE_ROWS` desc
