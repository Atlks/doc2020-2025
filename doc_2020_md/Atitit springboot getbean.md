Atitit springboot getbean



package org.chwin.firefighting.apiserver.data;

import com.google.common.collect.Maps;
import com.platform.top.xiaoyu.run.service.api.common.constant.ApiConstant;
import com.platform.top.xiaoyu.run.service.finance.controller.backstage.BankBindingController;
import com.top.xiaoyu.rearend.log.constant.TopLogConstant;
import ognl.Ognl;
import ognl.OgnlException;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.SpringCloudApplication;
import org.springframework.context.ConfigurableApplicationContext;
import org.springframework.context.annotation.ComponentScan;

import java.util.Map;


@ComponentScan(basePackages = {
   ApiConstant.BASE_PACKAGES,
   ApiConstant.BASE_PLATFORM_PACKAGES
})

@SpringBootApplication

public class SpringUtil {

   public static void main(String[] args) {
      //启动WEB项目
      SpringApplication  application = new SpringApplication(SpringUtil.class);
      ConfigurableApplicationContext context = application.run(args);
      System.out.println(context.getBean(  BankBindingController.class)  );

