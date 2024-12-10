Atitit 外键使用的问题以及解决


Cant create fk

ALTER TABLE `football_score_t` ADD CONSTRAINT `比赛关联` FOREIGN KEY (`match_id`) REFERENCES `basketball_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL;

 SET FOREIGN_KEY_CHECKS = 0;
ALTER TABLE `football_score_t` ADD CONSTRAINT `比赛关联` FOREIGN KEY (`match_id`) REFERENCES `basketball_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL;



Tmple insert

外键名字不能重复，哪怕跨表
外键查询
select t.id,t.for_name 子表for_name,c.for_col_name,t.ref_name 父表ref_name,c.ref_col_name from information_schema.INNODB_SYS_FOREIGN  t 
LEFT JOIN  information_schema.INNODB_SYS_FOREIGN_COLS  c on t.id=c.id
where t.id like '%kok%'
order by t.for_name


外键的异常捕获



{
	"@type":"org.apache.ibatis.exceptions.PersistenceException",
	"cause":{
		"@type":"java.sql.SQLIntegrityConstraintViolationException",
		"errorCode":1452,
		"localizedMessage":"Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)",
		"message":"Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)",
		"sQLState":"23000",
		"stackTrace":[{
			"className":"com.mysql.cj.jdbc.exceptions.SQLError",
			"fileName":"SQLError.java",
			"lineNumber":533,
			"methodName":"createSQLException",
			"nativeMethod":false
		}, ........................]
	},
	"localizedMessage":"\r\n### Error updating database.  Cause: java.sql.SQLIntegrityConstraintViolationException: Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)\r\n### The error may exist in mapper/FootballLiveMatchdetailliveDao.xml\r\n### The error may involve /.insert_into_football_tlive_t-Inline\r\n### The error occurred while setting parameters\r\n### SQL: insert   into football_tlive_t( id,time, type   ,data,position,match_id,main,   create_time,delete_flag)values(   replace(UNIX_TIMESTAMP(now(6)),'.',''),?,?,?,?,   ?,0,now(),0 )\r\n### Cause: java.sql.SQLIntegrityConstraintViolationException: Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)",
	"message":"\r\n...

{
	"detailMessage": "\r\n### Error updating database.  Cause: java.sql.SQLIntegrityConstraintViolationException: Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)\r\n### The error may exist in mapper/FootballLiveMatchdetailliveDao.xml\r\n### The error may involve /.insert_into_football_tlive_t-Inline\r\n### The error occurred while setting parameters\r\n### SQL: insert   into football_tlive_t( id,time, type   ,data,position,match_id,main,   create_time,delete_flag)values(   replace(UNIX_TIMESTAMP(now(6)),'.',''),?,?,?,?,   ?,0,now(),0 )\r\n### Cause: java.sql.SQLIntegrityConstraintViolationException: Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)",
	"cause": {
		"SQLState": "23000",
		"vendorCode": 1452,
		"detailMessage": "Cannot add or update a child row: a foreign key constraint fails (`dev_kok_sport`.`football_tlive_t`, CONSTRAINT `直播tlive比赛关联` FOREIGN KEY (`match_id`) REFERENCES `football_match_t` (`id`) ON DELETE SET NULL ON UPDATE SET NULL)",
		"stackTrace": [],
		"suppressedExceptions": []
	},
	"stackTrace": [],
	"suppressedExceptions": []
}
