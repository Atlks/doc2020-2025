Atitit spring unit test request reponse prblm

不知为什么  SpringJUnit4ClassRunner不能debug。。只好手动junit



<bean id="application.web.controller.BudanController" class="application.web.controller.BudanController"></bean>
<bean id="javax.servlet.http.HttpServletRequest" class="org.springframework.mock.web.MockHttpServletRequest"  ></bean>
<bean id="MockHttpServletResponse" class="org.springframework.mock.web.MockHttpServletResponse"  ></bean>



//   applicationContextTest  classpath*:/*.xml   "",
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = {"classpath:applicationContext.xml"})
@WebAppConfiguration

public class budanTest   {
	
	public static void main(String[] args) {
	//	SqlSessionFactory
		//SimpleDataSource
		 //连接本地的 Redis 服务
        Jedis jedis = new Jedis("localhost");
        // 如果 Redis 服务设置来密码，需要下面这行，没有就不需要
        // jedis.auth("123456"); 
        System.out.println("连接成功");
        //查看服务是否运行
        System.out.println("服务正在运行: "+jedis.ping());
      //  javax.servlet.http.HttpServletRequest
        
        
    		ApplicationContext ac = new ClassPathXmlApplicationContext("applicationContext.xml");
    		BudanController HKLhcSchedule1 = ac.getBean(BudanController.class);
    		System.out.println(HKLhcSchedule1.ajaxBudanList());
	}
	
