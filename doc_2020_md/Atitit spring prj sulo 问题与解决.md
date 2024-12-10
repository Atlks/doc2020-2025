Atitit spring prj sulo 问题与解决.docx
Atitit spring 问题与解决


Description:

Field req in com.kok.sport.controller.ApiController required a bean of type 'javax.servlet.http.HttpServletRequest' that could not be found.

The injection point has the following annotations:
	- @org.springframework.beans.factory.annotation.Autowired(required=true)


Action:

Consider defining a bean of type 'javax.servlet.http.HttpServletRequest' in your configuration.

Auto req ,but not spring boot as web prj

@MapperScan({ "com.kok.sport.utils", "com.kok.sport.utils.constant", "com.kfit.user","" ,"mapper" })
@SpringBootApplication(exclude = {org.springframework.boot.autoconfigure.security.servlet.SecurityAutoConfiguration.class,DruidDataSourceAutoConfigure.class})
//@SpringBootApplication
@PropertySource(value= {"classpath:/conf/errorCode.properties"})
@ComponentScan({"com.kok","com.kok.*"})
public class SportApplication
{
	  public static ConfigurableApplicationContext context;
    public static void main(String[] args) {
    	
    //	javax.servlet.http.HttpServletRequest
    	  context= new SpringApplicationBuilder(). sources(SportApplication.class).web(WebApplicationType.SERVLET) .run ( args);
    	           // .profiles("client")
    

RequestContextHolder
	@GetMapping("/queryCount")
	public int queryCount() throws Exception {
		HttpServletRequest req = ((ServletRequestAttributes) (RequestContextHolder.currentRequestAttributes())).getRequest();
		
		Map m = RequestUtil.getMap(req);

		return MybatisQueryUtil.queryCount(m, MybatisMapper1);

	}
Spring中获取request的几种方法，及其线程安全性分析 - 编程迷思 - 博客园
