Atitit code 范例 example  

 code 范例 example  更好一些，将最佳实践融入其中。。

Springboot
Springboot test,,springboot lazy load

/miniCodePrj/src/main/java/sprbtPKg/Application.java
Db query insert updt
Sprbtjdbc insert

	public static void main(String[] args) {
		// sqlSessionFactory=getSqlSessFctry(dataSource, UserMapper.class);
		// tk_ini(sqlSessionFactory);

		String driver = "com.mysql.jdbc.Driver";
		String url = "jdbc:mysql://localhost:3306/mysql?allowMultiQueries=true"; // 创建一个表示数据库路径的字符串
		String username = "root"; // 创建一个表示数据库用户名的字符串
		String password = ""; // 创建一个表示数据库密码的字符串
		DriverManagerDataSource dataSource = new DriverManagerDataSource(url, username, password);

		String tableName = "user";
		Map<String, Object> parameters_map = new HashMap<String, Object>(3);
		parameters_map.put("id", 123);
		parameters_map.put("first_name", "aaa");

		int i = insert(dataSource, tableName, parameters_map);

		System.out.println(i);
		System.out.println("f");

	}

	private static int insert(DriverManagerDataSource dataSource, String tableName,
			Map<String, Object> parameters_map) {
		SimpleJdbcInsert SimpleJdbcInsert1 = new SimpleJdbcInsert(dataSource).withTableName(tableName);
		Set st = parameters_map.keySet();

		List<String> columnNames = new ArrayList<String>();
		columnNames.addAll(st);
		SimpleJdbcInsert1.setColumnNames(columnNames);
		// SimpleJdbcInsert1.usingColumns(columnNames)
		int i = SimpleJdbcInsert1.execute(parameters_map);
		return i;
	}

Hbnt demo
Mybatis demo
Db acc code mybatis jsdbtmeplte hbnt
Hibernate code demo
MybatisTest


Httpclient demo
 	
    	String uri=rq.getRequestURI();
    	String query=rq.getQueryString();     
          String newUrl = targetHost+uri+"?"+query;
		CloseableHttpResponse response =HttpClients.createDefault().execute(new HttpGet(newUrl)) ;    

        return EntityUtils.toString(response.getEntity(), "UTF-8");
Other
ExcelUtil    export json list









Ref
Atitit mybatis helloworld

