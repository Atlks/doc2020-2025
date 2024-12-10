Atitit mybatis动态数据源



@Bean(name = "sqlSessionFactory")


public SqlSessionFactory sqlSessionFactory(@Qualifier("dataSource") DataSource dataSource) throws Exception {


final SqlSessionFactoryBean sessionFactory = new SqlSessionFactoryBean();


sessionFactory.setDataSource(dataSource);



/*设置mapper文件位置*/


sessionFactory.setMapperLocations(new PathMatchingResourcePatternResolver()


.getResources("classpath:base/com/zhuoli/service/springboot/mybatis/config/repository/mapper/*.xml"));



/*设置实体类映射规则: 下划线 -> 驼峰*/


org.apache.ibatis.session.Configuration configuration = new org.apache.ibatis.session.Configuration();


configuration.setMapUnderscoreToCamelCase(true);


sessionFactory.setConfiguration(configuration);


return sessionFactory.getObject();


}




