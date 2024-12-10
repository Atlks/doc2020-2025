Atitit nacos 问题解决



单机模式启动失败，报db.num is null等错误#4074

启动start.bat里面替换，，或者使用参数 -m standalone

Mode=standalone


# standalone模式启动
sh startup.sh -m standalone
5、进行访问
访问地址：IP:8848/nacos
默认账号：nacos
默认密码:nacos
结果如下所示：

　　启动服务器：nacos的默认端口是8848，需要保证8848默认端口没有被其他进程占用
　　　　启动命令：cmd startup.cmd 或者双击startup.cmd运行文件。
　　启动成功，可通过浏览器访问 http://127.0.0.1:8848/nacos
　　　　使用默认用户名：nacos，默认密码：nacos 登录即可打开主页面。
　　外部mysql数据库支持：单机模式时nacos默认使用嵌入式数据库实现数据的存储，若想使用外部mysql存储nacos数据，需要进行以下步骤：
　　　　1. 安装数据库，版本要求：5.6.5+ ，mysql 8 以下
　　　　2. 初始化mysql数据库，新建数据库nacos_config，数据库初始化文件已存放在安装目录中：/conf/nacos-mysql.sql
　　　　3. 修改 /conf/application.properties 文件，增加支持mysql数据源配

Eureka切换Nacos时发现两个注册中心的解决方法 - 简书

注意nacos有配置服务和服务注册服务，需要选择服务注册服务。。
但是不能喝eureka共存。。只好把pom里面eureka的start 应用删除掉就可以了。。。



om.netflix.client.ClientException: Load balancer does not have available #
已经解决了,谢谢,是因为服务名区分大小写,feign的name和服务名大小写不一致

Erreka无所谓大小写。。Nacos就不一样了。




