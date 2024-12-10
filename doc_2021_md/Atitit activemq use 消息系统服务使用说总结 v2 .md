Atitit activemq  消息系统服务使用说总结

1.1. 启动	1
1.2. 打开管理界面（管理界面可以查看并管理所有队列及消息）	1
1.3. 代码写消息 读取消息参考范例项目	1
1.4. 范例项目 C:\0wkspc\MqDemoPrj	1
1.5. 范例代码	1
1.6. 参考资料	2


启动
>C:\apache-activemq-5.14.4\bin\activemq.bat start

root of context hierarchy
 INFO | Using Persistence Adapter: KahaDBPersistenceAdapter[C:\apache-activemq-5.16.0\bin\..\data\kahadb]
 INFO | PListStore:[C:\apache-activemq-5.16.0\bin\..\data\localhost\tmp_storage] started
 INFO | Apache ActiveMQ 5.16.0 (localhost, ID:DESKTOP-LE76MSF-64411-1601455636626-0:1) is starting
 INFO | Listening for connections at: tcp://DESKTOP-LE76MSF:61616?maximumConnections=1000&wireFormat.maxFrameSize=104857600
 INFO | Connector openwire started
 INFO | Listening for connections at: amqp://DESKTOP-LE76MSF:5672?maximumConnections=1000&wireFormat.maxFrameSize=104857600
 INFO | Connector amqp started
 INFO | Listening for connections at: stomp://DESKTOP-LE76MSF:61613?maximumConnections=1000&wireFormat.maxFrameSize=104857600
 INFO | Connector stomp started
 INFO | Listening for connections at: mqtt://DESKTOP-LE76MSF:1883?maximumConnections=1000&wireFormat.maxFrameSize=104857600
 INFO | Connector mqtt started
 INFO | Starting Jetty server
 INFO | Creating Jetty connector
 WARN | ServletContext@o.e.j.s.ServletContextHandler@386f0da3{/,null,STARTING} has uncovered http methods for path: /
 INFO | Listening for connections at ws://DESKTOP-LE76MSF:61614?maximumConnections=1000&wireFormat.maxFrameSize=104857600
 INFO | Connector ws started
 INFO | Apache ActiveMQ 5.16.0 (localhost, ID:DESKTOP-LE76MSF-64411-1601455636626-0:1) started
 INFO | For help or more information please see: http://activemq.apache.org
 INFO | ActiveMQ WebConsole available at http://127.0.0.1:8161/
 INFO | ActiveMQ Jolokia REST API available at http://127.0.0.1:8161/api/jolokia/

打开管理界面（管理界面可以查看并管理所有队列及消息）

http://localhost:8161/
Admin
Admin


代码写消息 读取消息参考范例项目
放入100消息后管理界面


范例项目 C:\0wkspc\MqDemoPrj
范例代码
ActiveMQ消息队列的使用及应用 - 朱小杰 - 博客园.html  有代码片段 范例代码

参考资料
ActiveMQ消息队列的使用及应用 - 朱小杰 - 博客园.html
ActiveMQ的简单使用 - CSDN博客.html
ActiveMQ消息队列的使用及应用 - 朱小杰 - 博客园.html  有代码片段 范例代码


