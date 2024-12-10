Atitit 问题解决检查chklist  检查表





代码静态走查看流程逻辑

动态执行  单元测试通过 可以查看日志模式单元测试。。
日志是否清晰   包括http rest sql的请求与返回
Sql  ，sql返回条数，sql返回记录集（单条，或少量的多条）
子方法进入 退出 log
重要分支log。。Foreach block，，if else block..
最好可以幂等 可以重复安全的执行  重复执行三次测试
Api接口返回info一下
Trycatch 
Foreach 每个项目都要trycatch  ，continue 模式尽可能
优先处理重要流程
兜底try 流程

记录最好不要del，而是update stat模式。。。

健壮性  循环内部trycatch  continue模式。。



加钱必须放最后 ，扣钱先放。。。

Junit可以但是有时候麻烦的
Sql日志

log4j.logger.com.ibatis=DEBUG  


0:45:10,980 DEBUG org.apache.ibatis.logging.jdbc.BaseJdbcLogger - ooo Using Connection [com.alibaba.druid.proxy.jdbc.ConnectionProxyImpl@25ce435]_frmlog4j
20:45:10,980 DEBUG org.apache.ibatis.logging.jdbc.BaseJdbcLogger - ==>  Preparing: UPDATE eRROR_oRDER SET ERROR_cOUNT = ? WHERE PK = ? _frmlog4j
20:45:10,981 DEBUG org.apache.ibatis.logging.jdbc.BaseJdbcLogger - ==> Parameters: 5(Integer), 27008550005899267(String)_frmlog4j
20:45:10.981 [main] INFO  jdbc.sqlonly - UPDATE eRROR_oRDER SET ERROR_cOUNT = 5 WHERE PK = '27008550005899267' 

				frmlogback
20:45:10.988 [main] INFO  jdbc.sqltiming - UPDATE eRROR_oRDER SET ERROR_cOUNT = 5 WHERE PK = '27008550005899267' 
 {executed in 7 msec}








