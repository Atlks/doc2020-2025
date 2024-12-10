Atitit spring getbean

applicationContext



package com.wz;

import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;
import org.springframework.boot.web.servlet.ServletComponentScan;
import org.springframework.context.ConfigurableApplicationContext;
import org.springframework.scheduling.annotation.EnableScheduling;

import com.wz.controller.util.RdsUti;

import tk.mybatis.spring.annotation.MapperScan;

@SpringBootApplication(exclude= {DataSourceAutoConfiguration.class})
@MapperScan("com.wz.mapper")
@ServletComponentScan(basePackages = {"com.wz.listener","com.wz.filter"})
@EnableScheduling
public class StartApp {
 	private  static Log log = LogFactory.getLog(StartApp.class);
	public static	ConfigurableApplicationContext  appContext;
	public static void main(String[] args) {
		log.info("startapp main start");
		   appContext=	SpringApplication.run(StartApp.class,args);
			log.info("startapp main exit");
	}
}

但是这个不能再sprbttest 里面使用。。。
貌似没有执行启动初始化。。Log查看了。。。只好另外想办法
添加了对ApplicationContext的注入 推荐。

有人提到，想要获取ApplicationContext实例。于是，添加了对ApplicationContext的注入。
/**
 * 用于需要用到Spring的测试用例基类
 * 
 * @author lihzh
 * @alia OneCoder
 * @blog http://www.coderli.com
 */@RunWith(SpringJUnit4ClassRunner.class)@ContextConfiguration(locations = { "/spring/applicationContext.xml" })public class SpringTest {
@Autowiredprotected ApplicationContext ctx;



	@Autowired
	protected ApplicationContext appContext;
	
	private  static Log log = LogFactory.getLog(OpenCodeUtils.class);
	
	  
		@Test
		public void setKaijiangTime() {
			////String string = "2020-7-6 18:30:00";
		//	ConfigurableApplicationContext appContext = StartApp.appContext;
			DataSource ds=	appContext.getBean(DataSource.class);
		log.info(JSON.toJSONString(new JdbcTemplate(ds).queryForList("select 1")));	;
			
//			MockHttpServletRequest req=new MockHttpServletRequest();
//			//req.setParameter(name, value);
//		  List  li=    new OpenServerController().kaijiangTimeSet("30", "快乐28","2021-01-15","2021-01-19", 123, req);
//		  log.info( JSON.toJSONString(li,true)	);	
		  		
		}
	


