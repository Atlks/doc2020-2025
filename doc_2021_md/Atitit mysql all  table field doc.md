Atitit mysql all  table field doc



select table_name 表名,  table_comment 含义 from    	information_schema.`TABLES` 
WHERE
	table_schema = 'version5'



SELECT
	table_schema 数据库,
	table_name 表名,
	column_name 列名,
	is_nullable,
	data_type 数据类型,
	column_type 字段类型,
	column_key 主键,
	column_comment  注释含义
FROM
	information_schema. COLUMNS
WHERE
	table_schema = 'version5'
ORDER BY
	table_schema,
	table_name
