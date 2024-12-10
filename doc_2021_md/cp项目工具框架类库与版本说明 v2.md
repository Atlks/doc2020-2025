Atitit cp项目工具框架类库与版本说明

项目说明admin 后台管理  api h5调用的接口  pay支付  quartz 定时器

 源码大概看了下，IDE是eclipse的环境，数据库是mysql咯。。抽空我补齐下缺失的文档哈。。

 api应该是app用到的后端接口吧

 admin是管理 quatz是定时任务


 
Ide中的模块与项目打包运行方式

 APPLICATION-POM ..................................
 APPLICATION-COMMON ...............................
 APPLICATION-MODEL ................................
 APPLICATION-BASE .................................
 APPLICATION-SERVICE ..............................
 APPLICATION-MAPPER-GENERATOR .....................
 APPLICATION-ADMIN Maven Webapp ...................
 APPLICATION-API Maven Webapp .....................
 APPLICATION-QUARTZ Maven Webapp ..................
 APPLICATION-PAY Maven Webapp .....................
 APPLICATION-ADMIN Maven Webapp API ...............

项目体积

Pay项目应该百兆左右
重要工具与 中间件与类库与框架
开发环境ide eclipse
语言与sdk版本 java 7  jdk6  jdk7
HTTP Rest接口 Web容器  tomcat7   支持jdk1.6  1.7
数据库与数据库中间件 mybatis
 Rdbms数据库mysql版本是  5.6大概
Nosqldb redis-3.0.1
依赖管理 Maven版本3.6.3
定时调度  
quartz调度器 java
Scm源码控制管理 git
Git + ide git插件+gui git
Spring  shiro
推送？
