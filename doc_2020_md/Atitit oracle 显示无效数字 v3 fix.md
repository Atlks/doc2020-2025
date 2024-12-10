Atitit oracle 显示无效数字 v3 fix


where rownum<999


可能是连接字段的类型不同，。。
使用导出字段。。。
然后一个个的对比连接字段。。使用to_char等转型匹配即可。。亲身体验。。


SELECT
	table_name,
	column_name,
	data_type,
	(
		SELECT
			comments
		FROM
			user_col_comments
		WHERE
			table_name = user_tab_columns.table_name
and   user_col_comments.column_name=user_tab_columns.column_name
	) AS comments
FROM
	user_tab_columns
WHERE
	table_name = UPPER ('EZ_FLOW_DE_ACTIVITY')
ORDER BY
	column_name


