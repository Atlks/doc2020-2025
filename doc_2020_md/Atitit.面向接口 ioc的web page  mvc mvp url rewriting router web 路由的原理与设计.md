Atitit.面向接口的web 原理与设计重写 路由启动绑定配置url router rewriting urlpage  mvc mvp的 java c#.net php js 


原理 通过vm带入启动参数    制定ioc配置文件 绑定各项。。

<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<iframe src="<%=request.getContextPath()+aaaCfg.IocX4jobui.getCfgVal("merchant_center_left_menu")%>" height="700px" width="190px" align="left" frameborder="0" hspace="0" vspace="0"  scrolling="no" ></iframe>
作者:: 绰号:老哇的爪子 （ 全名：：Attilax Akbar Al Rapanui 阿提拉克斯 阿克巴 阿尔 拉帕努伊 ） 汉字名：ail，  EMAIL:1466519819@qq.com
转载请注明来源： http://blog.csdn.net/attilax


package aaaCfg;

import com.attilax.io.pathx;
import com.attilax.util.PropX;

/**
 * aaaCfg.IocX4jobui
 * @author Administrator
 *
 */
public class IocX4jobui {

	public static void main(String[] args) {
		System.out.println(aaaCfg.IocX4jobui.getCfgVal("hre_web_url"));

	}

	public static String getCfgVal(String string) {
		String x = "resin.server："+ System.getProperty("resin.server");
		System.out.println(x);
		 String apptype=System.getProperty("apptype");
		 String cfgpath=pathx.webAppPath()+"/"+apptype+".cfg.txt";
		 PropX px=new PropX(cfgpath);
		return px.getProperty(string);
	}

}


----------jobus.cftg.txt

hre_web_url=/CommonServletV2
#hre_web_url base /approot
#com.attilax.php/cms/CmsImp_4Imovie.php
#sql_query=select * from wxb_good_copy

merchant_center_left_menu=/customer/left_menu4jobus.jsp



----End




