Atitit springboot  helloword  最简化 attilax总结

1.1. 建立项目springboothelloword	1
1.2. 下载maven，通过maven下载springboot的jar。。当然也可以手动下载	1
1.3. 下载到的文件清单126个文件，24M 为了方便导入，从层级文件夹里面搜索出来	2
1.4. 把人maven仓库下载的springboot  jar 导入项目	6
1.5. 4、编制启动java  Application.java存于myFirstProject\src\main\java\com\example\myFirstProject下	6
1.6. 编制Example.java，	6
1.7. 运行 app java   解决了三个slf jar版本冲突问题，删了三个jar slf1.5的jar	7
1.8. 运行 app java 此时已经启动了，springboot默认集成了tomcat 已经启动了web服务	7
1.9. 测试 输入http://localhost:8080，显示如图6	8
1.10. 在浏览器中,输入http://localhost:8080/hello/SpringBoot	8
2. 附录	8
2.1. 错误排除	8
2.2. Slf1.5 问题，，里面有1.7的jar 也有1.5的，提示需要1.7的。。	8
2.3. SLF4J: Class path contains multiple SLF4J bindings.	8
2.4. Exception in thread "main" java.lang.NoSuchMethodError: org.slf4j.spi.LocationAwareLogger.log(Lorg/slf4j/Marker;Ljava/lang/String;ILjava/lang/String;Ljava/lang/Throwable;)V	9
2.5. Atitit maven使用总结attilax总结	10
3. 参考资料	10


建立项目springboothelloword
下载maven，通过maven下载springboot的jar。。当然也可以手动下载
D:\prgrm\apache-maven-3.5.0\bin\mvn.cmd -f D:\workspace\springboothelloword\down_springboot.txt test

下载jar配置文件参考 SpringBoot入门系列：第一篇 Hello World - CSDN博客.mhtml 	
貌似里面主要下载 org.springframework.boot 这类类库jar和依赖

默认maven 仓库配置文件maven/conf/ settings.xml
默认的maven仓库在  C:\Users\Administrator\.m2\repository


默认的仓库国外太慢，使用阿里云沟内的，速度块。。三十分钟都没下载完，使用阿里云这个仓库，三俩分就ok了
阿里云的Maven仓库地址如下：
http://maven.aliyun.com/nexus/#view-repositories;public~browsestorage
 
如何在Maven中配置使用呢？
很简单，在maven的settings.xml 文件里配置mirrors的子节点，添加如下mirror：
Html代码  
<span style="font-family: 'Microsoft YaHei', 微软雅黑, SimHei, tahoma, arial, helvetica, sans-serif;">  <mirror>  
        <id>nexus-aliyun</id>  
        <mirrorOf>*</mirrorOf>  
        <name>Nexus aliyun</name>  
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>  
    </mirror></span>  
 
下载到的文件清单126个文件，24M 为了方便导入，从层级文件夹里面搜索出来
以及包括了嵌入版的tomcat

 驱动器 D 中的卷是 p2soft
 卷的序列号是 9AD0-D3C8

 D:\workspace\springboothelloword\jars 的目录

2018/02/02  23:35    <DIR>          .
2018/02/02  23:35    <DIR>          ..
2018/02/02  23:30           331,716 backport-util-concurrent-3.1.jar
2018/02/02  23:10            64,804 classmate-1.3.1.jar
2018/02/02  23:27            37,854 classworlds-1.1.jar
2018/02/02  23:27            30,117 commons-cli-1.0.jar
2018/02/02  23:30           315,805 commons-lang3-3.1.jar
2018/02/02  23:29            44,598 commons-logging-api-1.1.jar
2018/02/02  23:27             5,936 doxia-sink-api-1.0-alpha-7.jar
2018/02/02  23:29           639,592 google-collections-1.0.jar
2018/02/02  23:13           704,465 hibernate-validator-5.2.4.Final.jar
2018/02/02  23:10            55,783 jackson-annotations-2.8.1.jar
2018/02/02  23:11           280,014 jackson-core-2.8.1.jar
2018/02/02  23:15         1,230,290 jackson-databind-2.8.1.jar
2018/02/02  23:35                 0 jars.txt
2018/02/02  23:09            66,802 jboss-logging-3.3.0.Final.jar
2018/02/02  23:30            16,722 jcl-over-slf4j-1.5.6.jar
2018/02/02  23:06            16,431 jcl-over-slf4j-1.7.21.jar
2018/02/02  23:29            31,866 jsr305-2.0.1.jar
2018/02/02  23:06             4,597 jul-to-slf4j-1.7.21.jar
2018/02/02  23:29           121,070 junit-3.8.1.jar
2018/02/02  23:29           120,640 junit-3.8.2.jar
2018/02/02  23:29           358,085 log4j-1.2.12.jar
2018/02/02  23:06            23,646 log4j-over-slf4j-1.7.21.jar
2018/02/02  23:08           304,075 logback-classic-1.1.7.jar
2018/02/02  23:08           470,782 logback-core-1.1.7.jar
2018/02/02  23:28            87,360 maven-artifact-2.0.6.jar
2018/02/02  23:29            88,909 maven-artifact-2.0.9.jar
2018/02/02  23:30            80,322 maven-artifact-2.2.1.jar
2018/02/02  23:29            56,508 maven-artifact-manager-2.0.6.jar
2018/02/02  23:29            57,835 maven-artifact-manager-2.0.9.jar
2018/02/02  23:30            67,574 maven-artifact-manager-2.2.1.jar
2018/02/02  23:03            42,949 maven-compiler-plugin-3.1.jar
2018/02/02  23:27           151,617 maven-core-2.0.6.jar
2018/02/02  23:29           159,630 maven-core-2.0.9.jar
2018/02/02  23:30           177,887 maven-core-2.2.1.jar
2018/02/02  23:27            13,612 maven-error-diagnostics-2.0.6.jar
2018/02/02  23:29            13,786 maven-error-diagnostics-2.0.9.jar
2018/02/02  23:30            13,022 maven-error-diagnostics-2.2.1.jar
2018/02/02  23:28            43,106 maven-filtering-1.1.jar
2018/02/02  23:28            86,390 maven-model-2.0.6.jar
2018/02/02  23:29            87,322 maven-model-2.0.9.jar
2018/02/02  23:30            87,588 maven-model-2.2.1.jar
2018/02/02  23:27            10,242 maven-monitor-2.0.6.jar
2018/02/02  23:29            10,281 maven-monitor-2.0.9.jar
2018/02/02  23:30            10,456 maven-monitor-2.2.1.jar
2018/02/02  23:30            14,039 maven-plugin-annotations-3.3.jar
2018/02/02  23:26            12,860 maven-plugin-api-2.0.6.jar
2018/02/02  23:29            12,892 maven-plugin-api-2.0.9.jar
2018/02/02  23:30            12,374 maven-plugin-api-2.2.1.jar
2018/02/02  23:27            36,872 maven-plugin-descriptor-2.0.6.jar
2018/02/02  23:29            37,043 maven-plugin-descriptor-2.0.9.jar
2018/02/02  23:30            39,285 maven-plugin-descriptor-2.2.1.jar
2018/02/02  23:27            20,756 maven-plugin-parameter-documenter-2.0.6.jar
2018/02/02  23:29            20,878 maven-plugin-parameter-documenter-2.0.9.jar
2018/02/02  23:30            22,192 maven-plugin-parameter-documenter-2.2.1.jar
2018/02/02  23:27            28,922 maven-plugin-registry-2.0.6.jar
2018/02/02  23:29            29,073 maven-plugin-registry-2.0.9.jar
2018/02/02  23:30            29,710 maven-plugin-registry-2.2.1.jar
2018/02/02  23:27            35,241 maven-profile-2.0.6.jar
2018/02/02  23:29            35,359 maven-profile-2.0.9.jar
2018/02/02  23:30            35,362 maven-profile-2.2.1.jar
2018/02/02  23:27           116,183 maven-project-2.0.6.jar
2018/02/02  23:29           121,780 maven-project-2.0.9.jar
2018/02/02  23:30           156,283 maven-project-2.2.1.jar
2018/02/02  23:27             9,941 maven-reporting-api-2.0.6.jar
2018/02/02  23:30            10,940 maven-reporting-api-3.0.jar
2018/02/02  23:27            24,475 maven-repository-metadata-2.0.6.jar
2018/02/02  23:29            24,559 maven-repository-metadata-2.0.9.jar
2018/02/02  23:30            25,656 maven-repository-metadata-2.2.1.jar
2018/02/02  23:02            29,519 maven-resources-plugin-2.6.jar
2018/02/02  23:27            49,100 maven-settings-2.0.6.jar
2018/02/02  23:29            49,112 maven-settings-2.0.9.jar
2018/02/02  23:30            49,042 maven-settings-2.2.1.jar
2018/02/02  23:29            13,538 maven-shared-incremental-1.1.jar
2018/02/02  23:29           154,519 maven-shared-utils-0.1.jar
2018/02/02  23:30           274,434 maven-surefire-common-2.18.1.jar
2018/02/02  23:04            37,015 maven-surefire-plugin-2.18.1.jar
2018/02/02  23:29            32,911 maven-toolchain-1.0.jar
2018/02/02  23:30            37,623 maven-toolchain-2.2.1.jar
2018/02/02  23:29             6,809 plexus-build-api-0.0.4.jar
2018/02/02  23:30            13,494 plexus-cipher-1.4.jar
2018/02/02  23:29            46,088 plexus-classworlds-2.2.2.jar
2018/02/02  23:29            24,990 plexus-compiler-api-2.2.jar
2018/02/02  23:29            18,971 plexus-compiler-javac-2.2.jar
2018/02/02  23:29             4,561 plexus-compiler-manager-2.2.jar
2018/02/02  23:29             4,211 plexus-component-annotations-1.5.5.jar
2018/02/02  23:29           194,185 plexus-container-default-1.0-alpha-9-stable-1.jar
2018/02/02  23:29           216,640 plexus-container-default-1.5.5.jar
2018/02/02  23:27            13,407 plexus-interactivity-api-1.0-alpha-4.jar
2018/02/02  23:30            50,936 plexus-interpolation-1.11.jar
2018/02/02  23:29            61,057 plexus-interpolation-1.13.jar
2018/02/02  23:30            28,555 plexus-sec-dispatcher-1.3.jar
2018/02/02  23:29           210,680 plexus-utils-1.5.1.jar
2018/02/02  23:30           228,110 plexus-utils-1.5.15.jar
2018/02/02  23:29           223,171 plexus-utils-2.0.5.jar
2018/02/02  23:30            22,338 slf4j-api-1.5.6.jar
2018/02/02  23:06            41,071 slf4j-api-1.7.21.jar
2018/02/02  23:30             8,815 slf4j-jdk14-1.5.6.jar
2018/02/02  23:10           273,599 snakeyaml-1.17.jar
2018/02/02  23:06           379,821 spring-aop-4.3.2.RELEASE.jar
2018/02/02  23:06           757,134 spring-beans-4.3.2.RELEASE.jar
2018/02/02  23:06           646,164 spring-boot-1.4.0.BUILD-20160728.175440-591.jar
2018/02/02  23:06           646,164 spring-boot-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06           931,886 spring-boot-autoconfigure-1.4.0.BUILD-20160728.175440-592.jar
2018/02/02  23:06           931,886 spring-boot-autoconfigure-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:02            62,035 spring-boot-maven-plugin-1.4.0.BUILD-20160728.175440-590.jar
2018/02/02  23:02            62,035 spring-boot-maven-plugin-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06             2,309 spring-boot-starter-1.4.0.BUILD-20160728.175440-590.jar
2018/02/02  23:06             2,309 spring-boot-starter-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06             2,328 spring-boot-starter-logging-1.4.0.BUILD-20160728.175440-590.jar
2018/02/02  23:06             2,328 spring-boot-starter-logging-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06             2,312 spring-boot-starter-tomcat-1.4.0.BUILD-20160728.175440-590.jar
2018/02/02  23:06             2,312 spring-boot-starter-tomcat-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06             2,363 spring-boot-starter-web-1.4.0.BUILD-20160728.175440-590.jar
2018/02/02  23:06             2,363 spring-boot-starter-web-1.4.0.BUILD-SNAPSHOT.jar
2018/02/02  23:06         1,133,137 spring-context-4.3.2.RELEASE.jar
2018/02/02  23:06         1,110,160 spring-core-4.3.2.RELEASE.jar
2018/02/02  23:06           263,693 spring-expression-4.3.2.RELEASE.jar
2018/02/02  23:06           811,682 spring-web-4.3.2.RELEASE.jar
2018/02/02  23:06           913,982 spring-webmvc-4.3.2.RELEASE.jar
2018/02/02  23:30           147,968 surefire-api-2.18.1.jar
2018/02/02  23:30            39,877 surefire-booter-2.18.1.jar
2018/02/02  23:22         2,978,551 tomcat-embed-core-8.5.4.jar
2018/02/02  23:07           239,714 tomcat-embed-el-8.5.4.jar
2018/02/02  23:10           241,285 tomcat-embed-websocket-8.5.4.jar
2018/02/02  23:09            63,777 validation-api-1.1.0.Final.jar
2018/02/02  23:29           133,826 xbean-reflect-3.4.jar
             126 个文件     22,466,663 字节
               2 个目录  2,392,588,288 可用字节


把人maven仓库下载的springboot  jar 导入项目
体积大概总共24M

文档内容从SpringBoot的文档拷贝
4、编制启动java  Application.java存于myFirstProject\src\main\java\com\example\myFirstProject下
[java] view plain copy
package com.example.myFirstProject;  
  
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
  
  
@SpringBootApplication  
public class Application {  
  
    public static void main(String[] args) {  
        SpringApplication.run(Application.class, args);  
    }  
}  
编制Example.java，
存于myFirstProject\src\main\java\com\example\myFirstProject下
[java] view plain copy
package com.example.myFirstProject;  
  
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;  
import org.springframework.web.bind.annotation.PathVariable;  
import org.springframework.web.bind.annotation.RequestMapping;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@EnableAutoConfiguration  
public class Example {  
      
    @RequestMapping("/")  
    String home() {  
        return "Hello World!";  
    }  
      
    @RequestMapping("/hello/{myName}")  
    String index(@PathVariable String myName) {  
        return "Hello "+myName+"!!!";  
    }  
}
运行 app java   解决了三个slf jar版本冲突问题，删了三个jar slf1.5的jar
运行 app java 此时已经启动了，springboot默认集成了tomcat 已经启动了web服务


  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v1.4.0.BUILD-SNAPSHOT)

2018-02-02 23:50:54.741  INFO 12556 --- [           main] com.example.myFirstProject.Application   : Starting Application on hmNotePC with PID 12556 (D:\workspace\springboothelloword\bin started by Administrator in D:\workspace\springboothelloword)
2018-02-02 23:50:54.745  INFO 12556 --- [           main] com.example.myFirstProject.Application   : No active profile set, falling back to default profiles: default
2018-02-02 23:50:54.877  INFO 12556 --- [           main] ationConfigEmbeddedWebApplicationContext : Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@293a5bf6: startup date [Fri Feb 02 23:50:54 GMT+08:00 2018]; root of context hierarchy
2018-02-02 23:50:58.457  INFO 12556 --- [   
测试 输入http://localhost:8080，显示如图6
在浏览器中,输入http://localhost:8080/hello/SpringBoot
附录
错误排除
Slf1.5 问题，，里面有1.7的jar 也有1.5的，提示需要1.7的。。
把1.5的slf api删除即可


SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/D:/workspace/springboothelloword/jars/logback-classic-1.1.7.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/D:/workspace/springboothelloword/jars/slf4j-jdk14-1.5.6.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [ch.qos.logback.classic.util.ContextSelectorStaticBinder]
Exception in thread "main" java.lang.NoSuchMethodError: org.slf4j.spi.LocationAwareLogger.log(Lorg/slf4j/Marker;Ljava/lang/String;ILjava/lang/String;Ljava/lang/Throwable;)V
	at org.apache.commons.logging.impl.SLF4JLocationAwareLog.warn(SLF4JLocationAwareLog.java:162)
	at org.springframework.boot.SpringApplicationRunListeners.callFinishedListener(SpringApplicationRunListeners.java:91)
	at org.springframework.boot.SpringApplicationRunListeners.finished(SpringApplicationRunListeners.java:72)
	at org.springframework.boot.SpringApplication.handleRunFailure(SpringApplication.java:810)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:324)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1185)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1174)
	at com.example.myFirstProject.Application.main(Application.java:11)


删除slf4j-jdk14-1.5.6.jar
Exception in thread "main" java.lang.NoSuchMethodError: org.slf4j.spi.LocationAwareLogger.log(Lorg/slf4j/Marker;Ljava/lang/String;ILjava/lang/String;Ljava/lang/Throwable;)V
	at org.apache.commons.logging.impl.SLF4JLocationAwareLog.warn(SLF4JLocationAwareLog.java:162)
	at org.springframework.boot.SpringApplicationRunListeners.callFinishedListener(SpringApplicationRunListeners.java:91)
	at org.springframework.boot.SpringApplicationRunListeners.finished(SpringApplicationRunListeners.java:72)
	at org.springframework.boot.SpringApplication.handleRunFailure(SpringApplication.java:810)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:324)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1185)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1174)
	at com.example.myFirstProject.Application.main(Application.java:11)

点击这个使用common loggin，发现来自与jar  jcl-over-slf4j-1.5.6  删除

Atitit maven使用总结attilax总结

Mvn.cmd  -f  pom7.xml  -s   d:/maven/conf/settings_repos2.xml test

-f 参数知名项目要用的jar配置文件 比如down_springboot.txt ，文件扩展名不被非得xml，TXT均可
-s 指明仓库位置，要把jar下载到那个目录

要下载某个jar，指南通过-f参数配置，不能直接指明名字
存储位置，也指南通过-s参数，无法命令行指明目录

-help 得到help

参考资料
参考 SpringBoot入门系列：第一篇 Hello World - CSDN博客.mhtml 	



作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王  纵火者 
简称：： st Emir Attilax Akbar 圣 埃米尔 阿提拉克斯 阿克巴
全名：：st Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 圣 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com


头衔：







 

转载请注明来源：attilax的专栏  http://blog.csdn.net/attilax
http://www.cnblogs.com/attilax/
Microblog
http://weibo.com/u/5941179815   (common attilax)
https://weibo.com/p/1005055941179815  （attilax201707,bek weibo）
http://weibo.com/u/5487832265 (tech,for blog auto gene)
知乎空间
https://www.zhihu.com/people/ati-att/activities
Qq 1466519819  小号112237553
 微信attilax  小号attilax201708
微博 attilax2016   小号attilax201707


--Atiend  v19

