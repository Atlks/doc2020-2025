Atitit json 格式化对象时间字段问题时间戳  数据库

Datetime查出来格式化后变成时间戳

使用转换字符串模式即可。。
CONCAT(trx_started,'') tm 



[13:46:24:670] [INFO] main - [
	{
		"trx_id":"412741393",
		"trx_state":"RUNNING",
		"trx_started":1611720293000,
		"trx_weight":2,
		"trx_mysql_thread_id":36233,
		"trx_tables_in_use":0,
		"trx_tables_locked":0,
		"trx_lock_structs":1,
		"trx_lock_memory_bytes":376,
		"trx_rows_locked":0,
		"trx_rows_modified":1,
		"trx_concurrency_tickets":0,
		"trx_isolation_level":"READ COMMITTED",
		"trx_unique_checks":1,
		"trx_foreign_key_checks":1,
		"trx_adaptive_hash_latched":0,
		"trx_adaptive_hash_timeout":10000,
		"trx_is_read_only":0,
		"trx_autocommit_non_locking":0,
		"tm":"2021-01-27 12:04:53"
	}
]
