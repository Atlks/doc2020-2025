Atitit 注册中心  eureka的使用

http://localhost:10800/eureka/apps
就能获得注册到EurekaServer的所有其他节点的信息


获取某个应用的所有实例信息：
http://localhost:10080/eureka/apps/应用名
获取某个应用的指定实例：
http://localhost:10080/eureka/apps/应用名/ip:port
获取某个实例的信息
http://localhost:10080/eureka/instances/ip:port
1） 获取所有服务的信息。
GET 请求： localhost:8076/eureka/apps
指定返回 xml 格式的数据，在请求头中添加下面2个：
Content-Type:application/json
Accept:application/xml
 
如果想返回json数据的格式，在请求头中添加下面2个即可：
Content-Type:application/json
Accept:application/json


使用 http 请求方式获取 eureka server的服务信息 - crazyCodeLove - 博客园
