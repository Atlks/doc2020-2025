Atitis mybatis的功能api扩展总结

MybatisAdvUtil

根据session得到所有配置

SqlSession conn = MybatisUtil.getConn();
	//	Configuration Configuration1 = checkSqlValds(conn);
		Configuration Configuration1=conn.getConfiguration();

Configuration1.getMappedStatement(sttID)
根据语句id得到sql

private static String getSqlBoundDefine(SqlSession conn, String sttID)  {
		 
		Configuration Configuration1 = conn.getConfiguration();
		// Configuration1.addLoadedResource(resource);

		// Configuration1.
		MappedStatement MappedStaement1 = Configuration1.getMappedStatement(sttID);
		DynamicSqlSource DynamicSqlSource1 = (DynamicSqlSource) MappedStaement1.getSqlSource();
		// DynamicSqlSource1.
		String fldname = "rootSqlNode";
		SqlNode SqlNode1 = (SqlNode) getFldValRE(DynamicSqlSource1, "rootSqlNode");
		MixedSqlNode MixedSqlNode1 = (MixedSqlNode) SqlNode1;
		List li = (List) getFldValRE(MixedSqlNode1, "contents");
		// StaticTextSqlNode <String,TextSqlNode> <TextSqlNode>

		Object r = li.stream().reduce("", (s, o) -> {

			String string = "";
			try {
				string = getFldVal(o, "text").toString();
			} catch (NoSuchFieldException | IllegalAccessException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			return s + string;
		});
		return r.toString();
	}

得到解析后的sql

private static String getSqlBound(SqlSession conn,String sttID) {
		Configuration Configuration1=conn.getConfiguration();

		MappedStatement MappedStaement1=	Configuration1.getMappedStatement(sttID);
		String sqlBound = MappedStaement1.getSqlSource().getBoundSql(null).getSql();
		return sqlBound;
	}

getXmlPath
	// mapper/ veDao.xml
	private static String getXmlPath(SqlSession conn, String sttID) throws Exception {
		Configuration Configuration1 = conn.getConfiguration();
		// Configuration1.addLoadedResource(resource);

		// Configuration1.
		MappedStatement MappedStaement1 = Configuration1.getMappedStatement(sttID);
	 
		// DynamicSqlSource1
		return MappedStaement1.getResource();
//		String sqlBound = MappedStaement1.getSqlSource().getBoundSql(null).getSql();
//		return sqlBound;
	}
