Atitit 性能与业务逻辑分析，，log4j 日志sql日志收集  打开



打开rest http日志

打开性能日志sql输出

Tk.mybatis


使用log4j.xml调整类半天打不开sql日志。。。
换成log4j.propertis终于ok类。。



# rootLogger sh new ,,,cate is old style
# log4j.rootCategory=INFO, stdout
log4j.rootLogger=debug, stdout
 

# \u63A7\u5236\u53F0\u8F93\u51FA
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
# log4j.appender.stdout.layout.ConversionPattern=%5p [%t] - %m%n
### \u8F93\u51FA\u4F4D\u7F6E ###
 
#log4j.appender.stdout.Target=System.out
 #%d time,,,%p level  %c logger  
log4j.appender.stdout.layout.ConversionPattern=%d{ABSOLUTE} %5p %C - %m%n

#----spring  
#log4j.logger.com.springframework=DEBUG,, stdout, spring
log4j.logger.org.springframework=info


#rest http api login
its ok...


#------------ sql loging
log4j.logger.application.dao=debug
logging.level.application.dao=debug
log4j.logger.com.xxx.mydao=DEBUG

log4j.logger.com.ibatis=DEBUG  
log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=DEBUG  
log4j.logger.com.ibatis.common.jdbc.ScriptRunner=DEBUG  
log4j.logger.com.ibatis.sqlmap.engine.impl.SqlMapClientDelegate=DEBUG  
log4j.logger.java.sql.Connection=DEBUG  
log4j.logger.java.sql.Statement=DEBUG  
log4j.logger.java.sql.PreparedStatement=DEBUG  
log4j.logger.java.sql.ResultSet=DEBUG
log4j.logger.org.apache.ibatis.logging.commons.JakartaCommonsLoggingImpl=DEBUG
log4j.logger.java.sql=DEBUG 

DEBUG [main] - ooo Using Connection [com.alibaba.druid.proxy.jdbc.ConnectionProxyImpl@237c8718]
DEBUG [main] - ==>  Preparing: SELECT ID,PLAY_gROUP_iD,NUMBER,OPEN_tIME,DATE,PRE_oPEN_cODE,UPDATE_tIME,COMPANY_sHORT_nAME,TOTAL_bET_mONEY,TOTAL_wIN_mONEY FROM sSC_oPEN_tIME WHERE ( PLAY_gROUP_iD = ? and NUMBER = ? ) limit ?,? 
DEBUG [main] - ==> Parameters: 6(Long), 2020002(String), 0(Integer), 1(Integer)


将sql带入到具体代码中
