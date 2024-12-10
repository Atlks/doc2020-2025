

主要分支   选择和循环



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
