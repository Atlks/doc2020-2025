Atitit spring单元测试 注解 获取服务名

Spring文件单独放在一个文件夹，去掉dubbo配置，方便测试
里面包含的mybatis 找不到，只好设置成相对于class绝对路径可以了

C:\0wkspc\clinical\target\classes\META-INF\springtest_cli\applicationContext-datasource.xml
	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="configLocation" value="C:\0wkspc\clinical\target\classes\META-INF\mybatis\mybatis-config.xml" />
		<property name="dataSource" ref="dataSource" />


服务名第一个字母小写。。


package com.cnhis.cloudhealth.clinical.autocharge;

import org.springframework.beans.BeansException;
import org.springframework.beans.factory.DisposableBean;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.context.support.FileSystemXmlApplicationContext;

import com.cnhis.cloudhealth.clinical.clidoctor.acolsetting.dao.IcolSettingDao;
import com.google.common.collect.Maps;

 

 

/**
 * v3 dir files  add
 * @author attilax
 *
 */
public class SpringUtilV3_prjcli implements ApplicationContextAware, DisposableBean {
	
	public static void main(String[] args) {
		// attilax 老哇的爪子  上午11:54:26   2014-5-14 
	//	SpringUtil.cfgFileDir=PathUtil.classPath_hisCommLib()+"/";
//		SpringUtil. locations =new  String[] {  PathUtil.classPath_hisCommLib()+"/"+"IocSrpingCfg.xml"};
//		annoTest bean = (annoTest) getBean("annoTest");
//		bean.someOp(56);
//		System.out.println(bean);
//		System.out.println("--");
		//branchManagerService
	//	SpringUtilV3.cfgFileDir="C:\\Users\\attilax\\Desktop\\springtest_cli";
		SpringUtilV3_prjcli.cfgFileDir="C:\\0wkspc\\clinical\\target\\classes\\META-INF\\springtest_cli";	
	//	SpringUtilV3.cfgFileDir="C:\\0wkspc\\clinical\\src\\main\\resources\\META-INF\\springtest_cli";	
		
		SpringUtilV3_prjcli.setLocations(cfgFileDir,"applicationContext-datasource.xml,onehis-dubbo.xml");
		IcolSettingDao d=	(IcolSettingDao) SpringUtilV3_prjcli.getBean("icolSettingDao");
		System.out.println(d.getSetting(Maps.newConcurrentMap()));

	}
