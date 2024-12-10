Atitit 提升开发效率 mvc 框架 java
Spark mvc   Supt htdpl

jfinal 框架    Supt htdpl 不推荐
需要web.xml麻烦

JFinal 是基于Java 语言的极速 web 开发框架，其核心设计目标是开发迅速、代码量少、学习简单、功能强大、轻量级、易扩展、Restful。在拥有Java语言所有优势的同时再拥有ruby、python等动态语言的开发效率。
Atitit jfinal mvc 使用 总结



1.使用JFinal框架集成的jetty server启动项目，JFinal提供了启动方法，示例：
public static void main(String[] args){
JFinal.start("WebRoot", 8080, "/", 5);
}
2.使用Tomcat等容器启动JFinal项目，如


http://localhost/hello

虽然是jetty  居然支持热部署。。厉害了。修改代码后直接生效

Loading changes ......
Loading complete.



个人刚接触到的一个——nutz 不推荐

需要配置web.xml
类似SSH的一个轻量级框架，只需要一个nutz.jar包，当然你还要自己导入数据库驱动和连接池
