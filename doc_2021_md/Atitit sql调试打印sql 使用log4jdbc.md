Atitit sql调试打印sql 使用log4jdbc

使用druid配置filter但是没有生效


	<property name="driverClassName"
			value="net.sf.log4jdbc.DriverSpy" />

		<property name="url"
			value="jdbc:log4jdbc:mysql://10.0.1.13:3306/cp?allowMultiQueries=true&amp;autoReconnect=true&amp; useUnicode=true&amp;characterEncoding=utf-8&amp;zeroDateTimeBehavior=convertToNull" />

Log4j 和logback.xml都配置了。。。俩个都有了

Logback里面都是sql对哈哈
