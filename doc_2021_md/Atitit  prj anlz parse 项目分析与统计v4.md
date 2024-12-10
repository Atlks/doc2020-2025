Atitit 项目分析与统计

静态分析+动态分析 。其中，
静态分析就是对代码的未执行阶段进行分析。说白了，就是分析一个工程的源码期，不涉及代码在执行阶段的表现。
动态分析就是对代码的执行阶段进行分析。


 模块分析，与模块位置idx
数据库分析 数据表的分类 日志表不断增长（包括用户表，订单表等）。。元数据表表 基本不增长。。。


编程语言类型与版本 

代码数量  ，格式


类库统记表  类型与版本
Thinkphp5 mvc frmwk
中间件 mq redis等

数据库数据库统计 类型 版本
 php 版本和mysql版本是？？数据库用的是mysql吧

 php要开启哪些类库模块还是默认即可
目录结构 说明 

## 目录结构

初始的目录结构如下：

~~~
www  WEB部署目录（或者子目录）==
|─base                  基础
|   |-autoload.php      自动加载类
|   |-BaseController    预留基类后续如需添加权限等功能可使用
|   |-MysqlInterface    mysql必须实现的接口
|
|-conf                  配置文件
|   |-db.php            数据库配置
|   |-publicKey.php     公钥 （预留）
|   
├─controller            逻辑处理
│  ├─Action.php         具体逻辑操作
│  ├─Curl.php           curl请求逻辑类
│  └─Verify.php         验证：加密等操作
│
├─core                  核心操作
│  ├─Mysql.php          Mysql CRUD基础操作类
|
|-exec.php              入口文件


空表数量等。。。
代码文件数量
项目体积
代码行数

一个能流行起来的成熟的开源项目必定功能齐全，可扩展，而功能齐全可扩展的开源项目必定很复杂，代码量大。比如Spring5框架的源码行数达到了六七十万行，SpringBoot的源码行数达到了25万行左右，Dubbo和RocketMQ的源码行数达到了10万行。一个成熟的开源项目代码量这么多，可以想象其有多复杂。

 


其他说明
编程范式 oop aop sp等
项目架构 web bs
核心模块架构图组成数量与关系
启动类入口
测试类

Apache配置 新端口启动

Listen 0.0.0.0:81
<VirtualHost *:81>
  ServerName localhost
  ServerAlias localhost
  DocumentRoot "${INSTALL_DIR}/www/_cms/"
  <Directory "${INSTALL_DIR}/www/_cms/">
    Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
   Require all granted
  </Directory>
</VirtualHost>

本地开发环境搭建文档流程
