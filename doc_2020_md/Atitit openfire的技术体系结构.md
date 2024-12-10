Atitit openfire的技术体系结构


(九)单台服务器支撑用户，上线初单台机器可以支撑6W+用户同时在线，优化后可支撑18W+，峰值可以支撑20W+，当前单台平均16W+，服务器配置Intel(R) Xeon(R) CPU 8核 + 16G内存

实openfire也没那么复杂，哈哈
底层的网络通讯细节都用mina屏蔽了，只关注XMPP协议及XEP的实现即可，精力全在业务逻辑了。 


（2）并发能力
　　Openfire的通信处理基于Apache MINA框架实现，单机可支持上万的并发，同时也支持集群。
（3）安全性：
　　XMPP在C2S通信，和S2S通信中都使用TLS协议作为通信通道的加密方法，保证通信的安全
（3）对Web的支持：
　　Openfire采用内置的jetty作web服务器，可以方便的在上面增加WEB功能。jetty服务器是随AdminConsolePlugin插件时启动，通过调用startup()方法。9090为其明文端口，9091为其加密端口。


