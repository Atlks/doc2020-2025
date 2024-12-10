

输出rest 和sql日志。。


要加title:contxt


Query要输出sql，list size，and restult
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
