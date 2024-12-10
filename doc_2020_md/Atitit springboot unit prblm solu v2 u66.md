Atitit springboot unit prblm solu


Enhance boot speed..def reg bean class


	public static void main(String[] args) {
		AnnotationConfigApplicationContext ctx = new AnnotationConfigApplicationContext();
		String basePackages = "com.kok.sport.utils.constant";
		// ctx.scan(basePackages);
		ctx.register(ServiceT.class);

		// ctx.register(org.apache.ibatis.session.defaults.DefaultSqlSession.class);
	//	ctx.register(SqlSessionImpAti.class);
		ctx.registerBean("SqlSession", SqlSession.class,new Supplier<SqlSession>() {

			@Override
			public SqlSession get() {
				 
				try {
					return MybatisUtil.getConn();
				} catch (Exception e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				return null;
			}
		} , SpringUtil.getBeanDef());
		ctx.register(SyncFootballBasicUpdateprofileServiImp.class);

		ctx.refresh();

		SyncFootballBasicUpdateprofileServiImp t = ctx.getBean(SyncFootballBasicUpdateprofileServiImp.class);
		try {
			t.session.getMapper(MybatisMapper.class).querySql("select 2");
			t.Football_Basic_Update_profile();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

    public static BeanDefinitionCustomizer getBeanDef() {
		return new BeanDefinitionCustomizer() {

			@Override
			public void customize(BeanDefinition bd) {
				// TODO Auto-generated method stub
				
			}};
	}

Cant find class,but can click can find the jar....
Solu...remove test scope
<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			 
		</dependency>


