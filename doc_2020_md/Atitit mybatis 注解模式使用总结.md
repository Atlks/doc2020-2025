Atitit mybatis3 注解模式使用总结


Mybatisdemo
/ormMybatis3demo/libs/mybatis-3.2.0-SNAPSHOT.jar

/ormMybatis3demo/src/db.properties
# Properties file for JDBC configuration
#
# Place this file in the root CLASSPATH

#MySQL Connection Configuration  
mysql.driver=org.sqlite.JDBC
mysql.url=jdbc:sqlite:D:\\000000\\mydatabase.sqlite
mysql.username=root
mysql.password=

ds =java\:/comp/env/jndi/wxb_site_newxxx


/ormMybatis3demo/src/pkg1/MapperCls.java

package pkg1;



import java.util.List;
import java.util.Map;

import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Param;
import org.apache.ibatis.annotations.Select;
import org.apache.ibatis.annotations.Update;

 

public interface MapperCls {
    
    /*
     * 这是基于注解的映射方式，实现对数据的增删改查，将sql语句直接写在注解的括号中
     * 这是一个接口，其不需要类去实现它
     * 下边分别是插入，删除，修改，查询一个记录，查询所有的记录
     * */
    
 
    
    @Select("${sql_intag}")
    public List<Map>   query(@Param("sql_intag") String sql);
    
 
    
}
/ormMybatis3demo/src/mybatis.xml

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration 
PUBLIC "-//mybatis.org//DTD Config 3.0//EN" 
"http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>

    <properties resource="db.properties"></properties>

	<settings>
	<!--   
		<setting name="defaultExecutorType" value="REUSE" />
		-->
		<setting name="defaultStatementTimeout" value="30000" />
	</settings>

	<!-- <plugins>
		<plugin interceptor="cn.freeteam.util.OffsetLimitInterceptor"> -->
			<!-- <property name="dialectClass" value="cn.freeteam.util.SQLServerDialect"/> -->
		<!--</plugin>
	</plugins> -->
	<environments default="mysql">
		 
		<environment id="mysql">
			<transactionManager type="JDBC" ></transactionManager>
			<dataSource type="POOLED">
				<property name="driver" value="${mysql.driver}" />
				<property name="url" value="${mysql.url}" />
				<property name="username" value="${mysql.username}" />
				<property name="password" value="${mysql.password}" />
				<property name="poolMaximumIdleConnections" value="0" />
				<property name="poolMaximumActiveConnections" value="10" />
			</dataSource>
		</environment>
	</environments>

	<mappers>
	 <mapper class="pkg1.MapperCls"/>
	
		
		<!--   
		 	<mapper resource="cn/freeteam/model/OperlogsMapper.xml"/>
		 	-->
	</mappers>	
</configuration>
mybatisdemo 


package pkg1;
import java.io.InputStream;
import java.util.List;

import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;

import com.alibaba.fastjson.JSON;

public class mybatisdemo {
	public static void main(String[] args) {

		String resource = "mybatis.xml";

		// 加载mybatis 的配置文件（它也加载关联的映射文件）
		InputStream is = mybatisdemo.class.getClassLoader().getResourceAsStream(resource);

		// 构建sqlSession 的工厂
		SqlSessionFactory factory = new SqlSessionFactoryBuilder().build(is);
		
		 SqlSession session=factory.openSession(true);
		 
		 MapperCls mapper=session.getMapper(MapperCls.class);
		 @SuppressWarnings("rawtypes")
	//	List li  =mapper.queryall();
 	 List li  =mapper.query("select * from tab1");
		 System.out.println( JSON.toJSONString(li));
		 session.close();
	//	= session.selectList(arg0);

	}

}

错误解决
mybatis The error may involve defaultParameterMap
    @Select("select  * from tab1")
public List<Map>   queryall();

要定义List<Map> ，不要只是list


org.apache.ibatis.reflection.ReflectionException: There is no getter for property named

解决方法:在参数前加@Param标签
public List<Userinfo> findAll(@Param("sname") String sname);
ref

Mybatis框架基于注解的方式，实对数据现增删改查 - G-&-D - 博客园.html
