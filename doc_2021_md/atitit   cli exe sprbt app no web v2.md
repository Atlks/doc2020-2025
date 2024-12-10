

No add staer in pom.xml

2.依赖管理
防止Spring引导应用程序启动嵌入式web服务器的最简单方法是不将web服务器启动器包含在我们的依赖项中。在Maven POM或Gradle构建文件中都不包含spring-boot-starter-web依赖项。
3.修改Spring Application
在Spring引导中禁用嵌入式web服务器的另一种方法是使用代码配置spring容器行为。我们可以使用SpringApplicationBuilder 构造器 :

// 构造spring boot 应用
new SpringApplicationBuilder(MainApplication.class)
  .web(WebApplicationType.NONE)
  .run(args);

1
2
3
4
5
或者我们可以配置SpringApplication ：

SpringApplication application = new SpringApplication(MainApplication.class);
application.setWebApplicationType(WebApplicationType.NONE);
application.run(args);

1
2
3
4
4.使用Application Properties配置文件
使用代码配置来禁用web服务器是硬编码方式。但是，如果我们想在特定的环境中创建web服务器呢?在这种情况下，我们可以使用Spring应用程序属性:

spring.main.web-application-type=none
1
或者:

spring:
  main:
    web-application-type: none
1
2
3
这种方法的好处是我们可以有条件地启用web服务器。使用Spring配置文件，我们可以控制不同部署中的web服务器行为。例如，我们可以让在开发中运行的web服务器仅公开指标或其他Spring端点（用于监控任务执行情况），而在生产中出于安全原因禁用它。

5.结论
创建不使用web服务器的Spring引导应用程序有很多原因。在本文中，我们介绍了实现此目的的多种方法。每一种方法都有其优点和缺点，所以应该选择最符合我们需要的方法。
————————————————
版权声明：本文为CSDN博主「kerongao」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/kerongao/article/details/109576388
