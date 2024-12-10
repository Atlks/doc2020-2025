Atitit springboot spring重要api


获得context


public class SportApplication
{
	  public static ConfigurableApplicationContext context;
    public static void main(String[] args) {
    	  context=SpringApplication.run(SportApplication.class, args);
    	MybatisMapper MybatisMapper1 = context.getBean(MybatisMapper.class);
    

获取bean context.getBean
