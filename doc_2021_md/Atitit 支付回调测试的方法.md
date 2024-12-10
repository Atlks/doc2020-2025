Atitit 支付回调测试的方法

相关数据库里面要有数据 订单  配置数据等。。

INSERT report_pay_online 
SET pk=UUID_SHORT(), pay_online_id=4,

order_money = '300.0000',

order_no = '202101311355785723903344640'
 


show global variables like '%timeout%';


select * from  report_pay_online

select * from  pay_online

select * from  pay_iplist

配置spring test测试controlr


package application.web.controller;

import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.mock.web.MockHttpServletRequest;
import org.springframework.test.context.ContextConfiguration;
import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;
import org.springframework.test.context.web.WebAppConfiguration;

import application.web.controller.util.PayUtil;
import application.web.tool.HttpUtil;

@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = {"classpath:applicationContextTest.xml"})
@WebAppConfiguration
public class TestNtf {

	

	@Autowired
	NotifyController NotifyController1;
	
	

	@org.junit.Test
	public void testXxklfNotify() {
		
		String ps= "money=300.00, order_sn=202101311355785723903344640, pay_money=300.00, pay_state=0, pay_time=1612079532, sign=c9a58286e78d07fcbf47e7979c7546d4, sys_order_sn=16120794826274692875";
	    	MockHttpServletRequest reque=new MockHttpServletRequest();
			HttpUtil. setReqParam(ps,reque);
			PayUtil.geneOrderSql("report_pay_online",ps);
			String body="";
			NotifyController1.xklfNotify(reque, body);
	}
	public static void main(String[] args) {
		String cfg="payType=bank_trans, merchantId=1077, key=XNKxJIXlVurmscq6, url=https://pay.cola22.com/api/index";
		cfg=cfg.replaceAll(",", "###").replaceAll("=", "=>").replaceAll(" ", "");
		System.out.println(cfg);

	}

}

日志输出记得打印sql


    <root><!-- 设置接收所有输出的通道 -->
        <level value="debug"/>
        <!-- 对应上面的appender -->
        <appender-ref ref="STDOUT"/>
        <appender-ref ref="DEBUG"/>
        <appender-ref ref="ERROR"/>
        <appender-ref ref="INFO"/>
        <appender-ref ref="WARN"/>
        <appender-ref ref="FATAL"/>
    </root>
    
     <logger name="org.springframework">
        <level value="error"></level>
    </logger>
    
      <logger name="org.mybatis">
        <level value="error"></level>
    </logger>
    
       <logger name="com.alibaba">
        <level value="error"></level>
    </logger>
    
    
