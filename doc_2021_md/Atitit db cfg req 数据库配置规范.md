Atitit db cfg req 数据库配置规范


Springboot
spring:
   datasource:
      url: jdbc:mysql:// allowMultiQueries=true
      username: admin
      password: houtai@33.com
      driver-class-name: com.mysql.cj.jdbc.Driver
      type: com.aliba

Mybatis
<environment id="mysql">
			<transactionManager type="JDBC" ></transactionManager>
			<dataSource type="POOLED">
				<property name="driver" value="com.mysql.cj.jdbc.Driver" />
				<property name="url" value="${mysql.url}" />
				<property name="username" value="${mysql.username}" />
				<property name="password" value="${mysql.password}" />
				<property name="poolMaximumIdleConnections" value="0" />
				<property name="poolMaximumActiveConnections" value="10" />
			</dataSource>
		</environment>

Jpa

添加了标准化属性javax.persistence.jdbc.driver，javax.persistence.jdbc.url，javax.persistence.jdbc.user，javax.persistence.jdbc.password，用于持久性单元和实体管理器工厂配置。
D:\prj\sport-service\k-sport-service\target\classes\META-INF\persistence.xml

<property name="javax.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver" />
    <property name="javax.persistence.jdbc.driver" value="oracle.jdbc.OracleDriver"/>
            <property name="javax.persistence.jdbc.url" value="jdbc:oracle:thin:@localhost:1521:orcl"/>
            <property name="javax.persistence.jdbc.user" value="scott"/>
            <property name="javax.persistence.jdbc.password" value="tiger"/>


	<persistence-unit name="wmsPersisteUnitName">
		<provider>org.apache.openjpa.persistence.PersistenceProviderImpl
		</provider>
		<!-- 
		<class>com.wms.jpa.model.User</class>
		<class>com.wms.jpa.model.Message</class>
		 openjpa.ConnectionDriverName or javax.persistence.jdbc.driver
		 	<properties>
			
			<property name="openjpa.ConnectionDriverName" value="com.mysql.cj.jdbc.Driver" />
		
			<property name="openjpa.ConnectionURL" value="" />
			<property name="openjpa.ConnectionUserName" value="" />
			<property name="openjpa.ConnectionPassword" value="" />
			
					<property name="openjpa.DynamicEnhancementAgent" value="false" />
		</properties>
		 -->
		 	<properties>
		
			<property name="openjpa.RuntimeUnenhancedClasses" value="RuntimeUnenhancedClassesModes.SUPPORTED" />	
	</properties>
	</persistence-unit>
	
