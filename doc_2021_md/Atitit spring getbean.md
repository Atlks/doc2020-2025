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



