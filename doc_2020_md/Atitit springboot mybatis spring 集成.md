Atitit springboot mybatis spring 集成

Springboot1.4   mybatis3.4.6  /springbootMybatis


设置mapper
package springbootMybatis;



import java.util.List;
import java.util.Map;

import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Param;
import org.apache.ibatis.annotations.Select;
import org.apache.ibatis.annotations.Update;
import org.mybatis.spring.SqlSessionTemplate;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Component;

@Mapper
@Component
//iocSpring5demo.MybatisMapperCls
public interface MybatisMapperCls {
	
	
	//@Autowired
	//public	SqlSessionTemplate sqlSessionTemplate1;
    
    /*
     * 这是基于注解的映射方式，实现对数据的增删改查，将sql语句直接写在注解的括号中
     * 这是一个接口，其不需要类去实现它
     * 下边分别是插入，删除，修改，查询一个记录，查询所有的记录
     * */
    
 
    
    @Select("${sql_intag}")
    public List<Map>   query(@Param("sql_intag") String sql);
    
 
    
}
、配置mybatis MybatisConfig 
首先需要配置数据源，本例使用c3p0

@Data
@EnableAutoConfiguration
public class MybatisConfig {
    @Autowired
    private ComboPooledDataSource dataSource;
--------------------- 



package springbootMybatis;

import javax.sql.DataSource;

import org.apache.ibatis.session.SqlSessionFactory;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.SqlSessionTemplate;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.support.PathMatchingResourcePatternResolver;
import org.springframework.core.io.support.ResourcePatternResolver;
import org.springframework.jdbc.datasource.DataSourceTransactionManager;

 

/**
 * @author tony ittimeline@163.com
 * @date 2018-02-24-上午11:13
 * @website wwww.ittimeline.net
 * @see
 * @since JDK8u162
 */
@Configuration
//@//Import(DruidDataSourceConfiguraiton.class)
//@MapperScan(basePackages ="springMybatis")
@EnableAutoConfiguration
public class MyBatisConfiguartion { 
	   
		@Bean
		public DataSource dataSource() {
			AtiDateSource instance = new AtiDateSource();
			return instance;
			// configure and return the necessary JDBC DataSource
		}
		

	    @Bean
	    public SqlSessionFactory getSqlSessionFactory(){
	        try {
	            SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
	            sqlSessionFactoryBean.setDataSource(dataSource());
	            return sqlSessionFactoryBean.getObject();
	        }catch (Exception e){
	            e.printStackTrace();
	            return null;
	        }
	    }
 
    /**
     *
     * @param sqlSessionFactory
     * @return
     */
    @Bean
    public SqlSessionTemplate sqlSessionTemplate(SqlSessionFactory sqlSessionFactory){
        return new SqlSessionTemplate(sqlSessionFactory);
    }


	
//	   @Bean
//	    public DataSource dataSource() {
//	        BasicDataSource dataSource = new BasicDataSource();
//
//	        dataSource.setDriverClassName("com.mysql.jdbc.Driver");
//	        dataSource.setUrl("jdbc:mysql://localhost:3306/mb?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8");
//	        dataSource.setUsername("");   // 这里填写数据库用户名
//	        dataSource.setPassword("");   // 这里填写数据库密码
//
//	        return dataSource;
//	    }
//
	   


//	    @Bean
//	    public SqlSessionFactoryBean sqlSessionFactoryBean() throws Exception {
//	        SqlSessionFactoryBean sessionFactory = new SqlSessionFactoryBean();
//	        sessionFactory.setDataSource(dataSource());
//	   //     sessionFactory.setTypeAliasesPackage("me.firstsnow.model");
//	        return sessionFactory;
//	    }
//

/*
 @Bean(name = "sqlSessionFactory")
 public SqlSessionFactory sqlSessionFactoryBean(DataSource dataSource){

  
*/

}
 Cotrol 


import java.util.List;
import java.util.Map;

import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpSession;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import com.alibaba.fastjson.JSON;

@RestController  
@EnableAutoConfiguration  
public class Cotrol {  
 
	
	@Autowired
	MybatisMapperCls MybatisMapperCls1;
      
    @RequestMapping("/")  
    public  String home(HttpServletRequest req) {  
    	
    	List<Map> message = MybatisMapperCls1.query("select * from user_tab");
		
    	//	userService.addUser("user2");
    		// 输出结果
    		System.out.println(  JSON.toJSONString(message));
        return "Hello World 22!";  
    }  
    
}


Spring Boot整合mybatis全注解入门教程 - yyhnap的博客 - CSDN博客.html
Spring Boot整合mybatis全注解入门教程 - yyhnap的博客 - CSDN博客.html
