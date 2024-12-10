

主要分支   选择和循环
重要流程for，选择流程打标
Prj quartz


Logger通配符模式通配符记录器名称

对于基于属性properties的配置，您只需简单地获取软件包名称，而无需使用任何通配符
log4j.logger.org.apache.http=info
包名模式就可以了。。


log4j.logger.org.apache.http.*=info
log4j.logger.org.apache.http*=info
log4j.logger.org.apache.http.*.*=info

输出rest 和sql日志。。


要加title:contxt


Query要输出sql，list size，and restult
如果result不长的话 10个以内

private List query(JdbcTemplate jdbcTemplate, String sql) {
		logger_log4j2.info(sql);
		List li = jdbcTemplate.queryForList(sql);
		logger_log4j2.info("li.size():"+li.size());
		if(li.size()<20)
		logger_log4j2.info(JSON.toJSONString(li,true));
		return li;
	}
Update 要sql ，影响行数

	private static List<Map<String, Object>> queryx(final Connection conn, String sql) throws SQLException {
		log.info(sql);  
		QueryRunner qr = new QueryRunner();
		List<Map<String, Object>>	 li=qr.query(conn,sql, new MapListHandler());
		log.info("li.size:"+li.size());  
		return li;
	}

	private static void update(Connection conn, String sql) throws SQLException {
		log.info(sql);  
		QueryRunner qr = new QueryRunner();
		int r=qr.update(conn, sql);
		log.info("updt rzt:"+r);
	}

记录流程与方法调用链
启动记录Line功能，这样可以得到调用方法流程

记录结果
可以吧结果查询打印。。比如增加前费用后，前后日志对比。。
或者开启result日志

输出格式 time thread msg logger line
时间  thread --- msg  <<<< 记录器  调用class和line
