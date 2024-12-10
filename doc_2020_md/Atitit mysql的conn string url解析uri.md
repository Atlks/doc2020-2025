Atitit mysql的conn string url解析uri


Mysql的conn url是个自定义uri规范，，非官方规范
解析的话使用了mysql的jdbc驱动里面应该有解析的类，果然被我找到了。。从driver类入手，步步查找



/bookmarksHtmlEverythingIndexPrj/src/aOPtool/MysqlConnUrlParse.java

	// String connString;
package aOPtool;

import com.mysql.cj.conf.ConnectionUrl;
import com.mysql.cj.conf.ConnectionUrlParser;
import com.mysql.cj.conf.url.SingleConnectionUrl;

public class MysqlConnUrlParse {

	public static void main(String[] args) {
		// String connString;
			String mysqlConnUrl = "jdbc:mysql://47.100.12.36:3306/tt_pre?user=root&password=hhh";
			
		ConnectionUrlParser connStringParser = ConnectionUrlParser.parseConnectionString(mysqlConnUrl);
		System.out.println(connStringParser);
	//	com.mysql.cj.conf.ConnectionUrlParser@246b179d :: 
//		{scheme: "jdbc:mysql:", 
//			authority: "47.100.12.36:3306", 
//			path: "tt_pre", 
//			query: "user=root&password=123456&userinfo=root:123456", 
//			parsedHosts: null, parsedProperties: null}

		
		
		
		
		SingleConnectionUrl ConnectionUrl2=new SingleConnectionUrl(connStringParser, null);
System.out.println(ConnectionUrl2);
	}

}



com.mysql.cj.conf.ConnectionUrlParser@246b179d :: {scheme: "jdbc:mysql:", authority: "47.100.12.36:3306", path: "tt_pre", query: "user=root&password=hhh", parsedHosts: null, parsedProperties: null}
com.mysql.cj.conf.url.SingleConnectionUrl@3d04a311 :: {type: "SINGLE_CONNECTION", hosts: [com.mysql.cj.conf.HostInfo@7a46a697 :: {host: "47.100.12.36", port: 3306, user: root, password: hhh, hostProperties: {DBNAME=tt_pre}}], database: "tt_pre", properties: {user=root, password=hhh}, propertiesTransformer: null}


Atitit  List of URI schemes - Wikipedia.mhtml

