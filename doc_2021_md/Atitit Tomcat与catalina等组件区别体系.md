Atitit Tomcat与catalina等组件区别体系



7

Tomcat-是一个Web服务器，它具有以下组件：-Catalina-Servlet容器名称-Jasper-JSP引擎-Coyote-HTTP连接器-Cluster-是用于管理大型应用程序的负载平衡器

46

Catalina是Tomcat的servlet容器。Catalina实现了针对Servlet和JavaServer Pages（JSP）的Sun Microsystems规范。在Tomcat中，Realm元素代表分配给这些用户的用户名，密码和角色（类似于Unix组）的“数据库”。Realm的不同实现方式允许Catalina集成到已经创建和维护了此类认证信息的环境中，然后使用该信息来实现Servlet规范中所述的Container Managed Security。
Coyote是Tomcat的连接器组件，它支持HTTP 1.1协议作为Web服务器。这允许Catalina（名义上是Java Servlet或JSP容器）还充当普通Web服务器，将本地文件用作HTTP文档。
土狼在特定的TCP端口上侦听到服务器的传入连接，并将请求转发到Tomcat引擎以处理请求并将响应发送回请求的客户端。另一个土狼连接器Coyote JK进行类似的侦听，但是使用JK协议将其请求转发到另一个Web服务器，例如Apache。这通常可以提供更好的性能。

