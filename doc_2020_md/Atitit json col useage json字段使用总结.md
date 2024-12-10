Atitit json col useage json字段使用总结

字段查询在navicate里面显示blob问题 cast  char解决
Gui browery hto is ok..


SELECT
	`sys_data`.`id` AS `id`,
	json_unquote (
		json_extract (`sys_data`.`data`, '$.tab')
	) AS `tab`,
	cast(
		json_unquote (
			json_extract (`sys_data`.`data`, '$.dbid')
		) AS CHAR charset utf8
	) AS `dbid`,
	cast(
		json_unquote (
			json_extract (`sys_data`.`data`, '$.url')
		) AS CHAR charset utf8
	) AS `url`
FROM
	`sys_data`
WHERE
	(
		json_unquote (
			json_extract (`sys_data`.`data`, '$.tab')
		) = 'dbiddef'
	)


查询  select  data->>'$.dbid',data->>'$.ref_table'  from sys_data

设置col json key val

UPDATE sys_data SET `data` = JSON_SET(`data`,'$.table', 'sys_tab','$.rectype','table_ref' ) WHERE id = 6;
