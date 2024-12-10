Atitit jdbcTemplate


	@Test
	public void testJbbcQuery() {
		ApplicationContext ac = new ClassPathXmlApplicationContext("applicationContext.xml");


		//获取IoC容器中JdbcTemplate实例
	  JdbcTemplate jdbcTemplate=(JdbcTemplate) ac.getBean("jdbcTemplate");
		 String sql="insert into user (name,deptid) values (?,?)";
		 sql="select 2";
		//6 int count= jdbcTemplate.update(sql, new Object[]{"caoyc",3});
	log.info	(jdbcTemplate.dd(sql));
		
	   log.info("---");
	}
	
