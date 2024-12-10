Atitit atlog prblm 日志问题解决

Prj quartz


Log4j不能打出日志  log4jdbc

去除logbcack。Xml文件，

log4jdbc.log4j.properties

配置pom
    <!-- https://mvnrepository.com/artifact/com.googlecode.log4jdbc/log4jdbc -->
<dependency>
    <groupId>com.googlecode.log4jdbc</groupId>
    <artifactId>log4jdbc</artifactId>
    <version>1.2</version>
</dependency>
    
    
  <dependency>  
    <groupId>org.bgee.log4jdbc-log4j2</groupId>
    <artifactId>log4jdbc-log4j2-jdbc3</artifactId>
    <version>1.16</version>
</dependency>  
<dependency>  
    <groupId>org.slf4j</groupId>
    <artifactId>jcl-over-slf4j</artifactId>
    <version>1.7.2</version>
</dependency>  
<dependency>  
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>1.7.2</version>
</dependency>  
<dependency>  
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.2</version>
</dependency>  
 

