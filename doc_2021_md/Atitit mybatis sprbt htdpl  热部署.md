Atitit mybatis sprbt htdpl  热部署  

每次重新构建sqlfactory即可

@Autowired
	@Qualifier("ds2")
	private DataSource dataSourceDb2;

	@Bean(name = "sqlSessionFactoryDb2")
	public SqlSessionFactory sqlSessionFactoryDb2() throws Exception {
		SqlSessionFactoryBean factoryBean = new SqlSessionFactoryBean();
		factoryBean.setDataSource(dataSourceDb2);
		factoryBean.setMapperLocations(
				new PathMatchingResourcePatternResolver().getResources("classpath:mapper/**/*.xml"));
		return factoryBean.getObject();
	}

	@Bean
	public SqlSessionTemplate sqlSessionTemplateDb2() throws Exception {
		return new SqlSessionTemplate(sqlSessionFactoryDb2());
	}
