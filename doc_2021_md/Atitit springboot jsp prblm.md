Atitit springboot jsp prblm 


热部署

/deadlockchk/src/test/resources/application.properties
# 开启jsp页面的热部署
server.servlet.jsp.init-parameters.development=true


	<!--   hot deploy -->
	<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-devtools</artifactId>
   <optional>true</optional>
</dependency>

Pom


	<!--   hot deploy -->
	<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-devtools</artifactId>
   <optional>true</optional>
</dependency>
	
	<!--WEB支持-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<!--jsp页面使用jstl标签-->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
</dependency>

<!--用于编译jsp-->
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
    <scope>provided</scope>
</dependency>
	
/deadlockchk/src/main/webapp/t.jsp
Jsp方法  <%!  %>

<%@page import="org.springframework.test.jdbc.JdbcTestUtils"%>
<%@page import="javax.sql.DataSource"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<%! String halo(){
	DataSource ds=null;
  //  JdbcTestUtils
	System.out.println("");
  return "hhh";
	}
	%>
 
<%=halo() %>
</body>
</html>

http://localhost:8080/t.jsp
Jsp语法提示的问题。。Eclipse插件即可
