Atitit mybatis prblm n solu v1 u55


加载任意文职cfg
	public static SqlSessionFactory getSqlSessionFactory() throws Exception {
		String mybatisCfg_result = getCfgTxtV2();

		// System.out.println(mybatisCfg_result);
		InputStream is2 = new ByteArrayInputStream(mybatisCfg_result.getBytes());
		// ����sqlSession �Ĺ���
		return new SqlSessionFactoryBuilder().build(is2);
	}

根据dburl获取factory
	
	public static SqlSessionFactory getSqlSessionFactoryByDburl(String dburl) {
		String mybatisCfg_result = getCfgTxtByDburl(dburl.trim());

		// System.out.println(mybatisCfg_result);
		InputStream is2 = new ByteArrayInputStream(mybatisCfg_result.getBytes());
		// ����sqlSession �Ĺ���
		return new SqlSessionFactoryBuilder().build(is2);
	}

	private static String getCfgTxtByDburl(@NotNull @NonNull String mysqlConnUrl) {
		String mybatisCfg_result = null;
		try {
			mybatisCfg_result = mybatisCfgTxt();
		} catch (IOException e) {
			ExUtilV2t33.throwExV2(e);
		}

		//	String getCfgFile = SpringUtil.getCfgFile();
			String propFilePath = "/cfg";
			 
			ConnectionUrlParser connStringParser = ConnectionUrlParser.parseConnectionString(mysqlConnUrl);
			System.out.println(connStringParser);

			Object url = mysqlConnUrl;
			Object usr = UrlUtil.parse4Q(connStringParser.getQuery()).get("user");
			Object pwd = UrlUtil.parse4Q(connStringParser.getQuery()).get("password");
			if (pwd == null)
				pwd = "";
			url = cn.hutool.core.util.XmlUtil.escape(url.toString() + "&allowMultiQueries=true");

			mybatisCfg_result = mybatisCfg_result.replaceAll("\\$\\{mysql.url}", url.toString());
			mybatisCfg_result = mybatisCfg_result.replaceAll("\\$\\{mysql.username}", usr.toString());

			mybatisCfg_result = mybatisCfg_result.replaceAll("\\$\\{mysql.password}", pwd.toString());
			return mybatisCfg_result;
	//	return null;
	}

Load any mapper file
Or change cfg file  gvet factory new

			// Configuration.addLoadedResource
			SqlSessionFactory sqlSessionFactory = MybatisUtil.getSqlSessionFactory(li);
//		cfg on effect in ini factory
			// Configuration c= sqlSessionFactory.getConfiguration();
//			 for (String mpXmlPathRes : li) {
//				 c.addLoadedResource(mpXmlPathRes);
//			}

	public static SqlSession getConn(String mpXmlPathRes) {
		try {
			// Configuration.addLoadedResource
			SqlSessionFactory sqlSessionFactory = MybatisUtil.getSqlSessionFactory();
			Configuration c = sqlSessionFactory.getConfiguration();

			c.addLoadedResource(mpXmlPathRes);
Rebulider fac...
			SqlSession session = sqlSessionFactory.openSession(true);

			return session;
		} catch (Exception e) {
			throw new RuntimeException(e);
		}

	}

纯java配置Configuration
可以用来构造factory，就是太复杂了，建议jiazai after,then chagnge some cfg..then rebuild...to fac..

Debug

		SqlSession conn = MybatisUtil.getConn(li);
		Collection<MappedStatement> mappedStatements = conn.getConfiguration().getMappedStatements();
		for (MappedStatement mappedStatement : mappedStatements) {
			System.out.println("--------------------------");

			System.out.println("StatementType:    " + mappedStatement.getStatementType());
			System.out.println("id:    " + mappedStatement.getId());
			System.out.println("res:    " + mappedStatement.getResource());
			// System.out.println("getBoundSql:
			// "+mappedStatement.getBoundSql(null).getSql());
		}
		System.out.println(mappedStatements);
Other

	protected static void checkSqlValid(String sql, MappedStatement s) {
		if (sql == "")
			return;
		try {
			SQLStatementParser parser = new MySqlStatementParser(sql);

			// 使用Parser解析生成AST，这里SQLStatement就是AST
			SQLStatement statement = parser.parseStatement();
			System.out.println("---check ok");
			System.out.println(statement);
			System.out.println(s.getResource());
			System.out.println(sql);
			System.out.println("---check ok end");
		} catch (Exception e) {
			System.out.println("---check err");
			System.out.println(s.getResource());
			System.out.println(sql);
			System.out.println("---check err end");
			throw e;
		}

		;

	}
	private static String getSqlBound(SqlSession conn, String sttID, Map m) {
		Configuration Configuration1 = conn.getConfiguration();

		MappedStatement MappedStaement1 = Configuration1.getMappedStatement(sttID);
		String sqlBound = MappedStaement1.getSqlSource().getBoundSql(m).getSql();
		return sqlBound;
	}
