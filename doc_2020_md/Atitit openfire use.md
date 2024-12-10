Atitit openfire use


　3、通信机制
　　1、帐号体系
　　（1）XMPP服务器的帐号基础，是域（Domain），例如：org.example.com，它在服务器配置时的时候设置，也是服务器能被访问到的域名或IP地址。客户端连接的时候，用这个域去寻找服务器。
　　（2）JID：XMPP中，任何一个可能进行通信的实体，包括一个用户、或者一个聊天室，都需要一个JID。
　　用户的JID格式为：usre@domain，如：abc@org.example.com
　　聊天室的JID为：room@conference.domain， 如ABC@conference.org.example.com
　　一般情况，JID后面还会附带一个资源名（resource），指代这个客户端的来源，比如：abc@org.example.com/pc-abc，表示这个JID在一台名为pc-abc的设备上登录。这是同一个帐号能够在多个设备中登录的基础。
　　2、通信端口
　　C-S连接的端口是5222 ，S-S连接的端口为5269，这些端口已经在IANA注册。
　　3、通信机制
　　当客户端连接上XMPP服务器创建会话时，首先是建立一个TCP长连接，并在这个连接上收发XML流进行协商，协商通过后，服务端与客户端，可以通过Message、Presence、IQ这三种格式进行数据交换。

