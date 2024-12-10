Atitit.mybatis的测试  以及spring与mybatis在本项目中的集成配置说明


/AtiPlat_train/src/com/attilax/db/mybatisTO91.java

	
	 @SuppressWarnings("all")
	public static void main(String[] args) throws IOException {
	       // TODO Auto-generated method stub
	     
	           String resource = "com/attilax/db/ibatiascfg.xml";
	           Reader reader;


	           reader = Resources.getResourceAsReader(resource);


	           SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder()
	                   .build(reader);
	           SqlSession sqlSession = sqlSessionFactory.openSession();
	       List li=   sqlSession.selectList("getLockTables", 9999999);
//	            StudentDao studentDao =sqlSession.getMapper(StudentDao.class);
//	            Student st = studentDao.getstudent(1);
            System.out.println( li.size());
	           
	           List li2=    sqlSession.selectList("findRecords"," select 1 as tit ");
	           System.out.println(core.toJsonStrO88(li2));
	           
	       }


Spring的数据源配置
D:\0workspace\AtiPlatf_train\src\applicationContext.xml

<context:property-placeholder location="classpath:jdbc.properties"/>
   <!-- ati add q213 -->
   <bean id="dataSource"   
	  class="org.springframework.jdbc.datasource.DriverManagerDataSource">   
    <property name="driverClassName" value="${ct.jdbc.driverClassName}" />
    <property name="url" value="${ct.jdbc.url}" />



Mybatis配置文件的位置
 <!-- 数据访问入口 -->
    <bean id="sqlMapClient" class="org.springframework.orm.ibatis.SqlMapClientFactoryBean" p:configLocation="classpath:/config/ibatis/sql-map-config.xml" p:dataSource-ref="dataSource"/>
    
