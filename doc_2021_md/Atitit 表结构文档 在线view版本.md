Atitit 表结构文档 在线view版本


SELECT
	`c`.`TABLE_SCHEMA` AS `数据库`,
	`c`.`TABLE_NAME` AS `table_name`,
	`t`.`TABLE_COMMENT` AS `table_comment`,
	`c`.`COLUMN_NAME` AS `列名`,
	`c`.`COLUMN_COMMENT` AS `注释含义` 
FROM
	(
		`information_schema`.`columns` `c`
		LEFT JOIN `information_schema`.`tables` `t` ON ((
				`t`.`TABLE_NAME` = `c`.`TABLE_NAME` 
			))) 
WHERE
	(
	`c`.`TABLE_NAME` IN ( 'ssc_play_pl_group', 'ssc_play_pl_company', 'ssc_play_pl', 'ssc_play' )) 
ORDER BY
	`c`.`TABLE_SCHEMA`,
	`c`.`TABLE_NAME`
