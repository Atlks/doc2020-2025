Atitit 账户与支付系统部署说明总结



支付系统搭建与部署
2018-11-30 00:52:16
 70418 |  29 |  9
1. 开发工具
 eclipse、git或svn、maven

2. 技术框架
    核心框架：Spring Framework 3.2.4
    持久化框架：MyBatis 3.4.
    安全框架：Apache Shiro 1.2.5
    日志管理：SLF4J 1.7.21、Log4j 1.2.17
    数据库连接池：Druid 1.0.19    
    消息总线：ActiveMQ 5.11.4
    工具包：fastjson 1.2.11 
    jQuery 框架：DWZ

3. 系统运行环境
    3.1 软件环境：
        MySQL
        JDK1.7或以上
        apache-tomcat-7.0或其他容器
        ActiveMQ 5.11
    3.2 硬件环境(最小配置)：
        CPU：1核
        内存：1G

4. 安装部署
    4.1 说明
        运营管理系统登录账号密码：admin/123456
        商户后台系统登录账号密码：在boss运营后台添加用户时录入手机和密码
        roncoo-pay-common-core：公共类工程，不用单独部署
        roncoo-pay-service：核心业务类工程，不用单独部署
        roncoo-pay-app-notify：通知应用工程，独立jar方式启动
        roncoo-pay-app-reconciliation：对账应用工程，独立jar方式启动
        roncoo-pay-app-settlement：结算应用工程，独立jar方式启动
        roncoo-pay-web-boss：运营管理后台，部署tomcat启动
        roncoo-pay-web-gateway：支付网关工程，部署tomcat启动
        roncoo-pay-web-sample-shop：模拟商城工程，部署tomcat启动
        roncoo-pay-web-merchant：商户后台工程，部署tomcat启动
    4.2 步骤
        4.2.1 创建数据库，导入初始化脚本《database.sql》
        4.2.2 修改系统数据库连接roncoo-pay-service/src/main/resources/jdbc.properties
        4.2.3 从roncoo-pay-service工程的lib文件夹下加载支付宝支付sdk“alipay-sdk-java20151021120052.jar”和
        “alipay-trade-sdk.jar”
        4.2.4 下载ActiveMQ 5.11并安装，修改MQ配置roncoo-pay-service/src/main/resources/ mq_config.properties，
               以独立jar方式启动roncoo-pay-app-notify工程
             （注：商户通知是独立的一块，不影响支付及其他功能，可以省略该步骤）
        4.2.5 以独立jar方式启动roncoo-pay-app-settlement工程
        4.2.6 修改对账文件下载后存放地址roncoo-pay-service/src/main/resources/reconciliation_config.properties，
               以独立jar方式启动roncoo-pay-app-reconciliation
        4.2.7 添加支付宝和微信测试账号信息roncoo-pay-service/src/main/resources/alipay_config.properties
               和weixinpay_config
            （注：不需要本地测试支付，可以省略该步骤）
        4.2.8 通过mvn install命令打包编译系统
        4.2.9 拷贝roncoo-pay-web-boss.war、roncoo-pay-web-gateway.war、roncoo-pay-web-sample-shop.war、roncoo-pay-web-merchant.war至tomcat启动

