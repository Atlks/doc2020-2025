Atitit spring启动速度  随时注册bean


package com.wz.util;

import java.util.function.Supplier;

import javax.servlet.ServletContext;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.sql.DataSource;

import org.springframework.beans.factory.config.BeanDefinition;
import org.springframework.beans.factory.config.BeanDefinitionCustomizer;
import org.springframework.beans.factory.support.DefaultListableBeanFactory;
import org.springframework.beans.factory.support.GenericBeanDefinition;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.mock.web.MockHttpServletRequest;
import org.springframework.mock.web.MockHttpServletResponse;
import org.springframework.mock.web.MockServletConfig;
import org.springframework.mock.web.MockServletContext;
import org.springframework.web.context.support.AnnotationConfigWebApplicationContext;

 
import com.wz.StartApp;

public class SprUti {

	@SuppressWarnings("all")
	public static void main(String[] args) {
		//AnnotationConfigApplicationContext  AnnotationConfigWebApplicationContext
	//
		AnnotationConfigApplicationContext  applicationContext = new AnnotationConfigApplicationContext();
		DefaultListableBeanFactory beanFactory = (DefaultListableBeanFactory) applicationContext.getBeanFactory();

		applicationContext.register(Bean1.class);applicationContext.register(Bean1.class);
	//	applicationContext.scan("com.wz");	 
		setWebBean(applicationContext);
//		applicationContext.setServletContext(new MockServletContext());

		
		// applicationContext.register(StartApp.class);

	   	applicationContext.refresh();

		Bean1 h = (Bean1) applicationContext.getBean(Bean1.class);

		h.testBean();

	//	System.out.println(applicationContext.getBean(DataSource.class));
		
//		GenericBeanDefinition beanDefinition = new GenericBeanDefinition();
//		beanDefinition.setBeanClass(Bean1.class);
//		beanFactory.registerBeanDefinition("testxKaijyoTime开奖时间2idid", beanDefinition);
		// beanFactory.registers
		
	
		
		
		
	}

	private static void setWebBean(AnnotationConfigApplicationContext applicationContext) {
		applicationContext.registerBean("HttpServletResponse", javax.servlet.http.HttpServletResponse.class,
		new Supplier<HttpServletResponse>() {

			@Override
			public HttpServletResponse get() {

				return new MockHttpServletResponse();
			}
		}, new BeanDefinitionCustomizer() {

			@Override
			public void customize(BeanDefinition bd) {
				// TODO Auto-generated method stub
				
			}});

		applicationContext.registerBean("httpServletRequest", javax.servlet.http.HttpServletRequest.class,
				new Supplier<HttpServletRequest>() {

					@Override
					public HttpServletRequest get() {

						return new MockHttpServletRequest();
					}
				}, new BeanDefinitionCustomizer() {

					@Override
					public void customize(BeanDefinition bd) {
						// TODO Auto-generated method stub
						
					}});
		applicationContext.registerBean("MockServletContext", javax.servlet.ServletContext.class,
				new Supplier<ServletContext>() {

					@Override
					public ServletContext get() {

						return new MockServletContext();
					}
				}, new BeanDefinitionCustomizer() {

					@Override
					public void customize(BeanDefinition bd) {
						// TODO Auto-generated method stub
						
					}});
	}

}

