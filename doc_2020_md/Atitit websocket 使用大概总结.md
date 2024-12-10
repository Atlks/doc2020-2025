Atitit websocket 使用大概总结


使用场景

websocket 实时信息的Web应用却带来了很大的不便，如带有即时通信、实时数据、订阅推送等功能的应 用
实时数据可以用来更新缓存

三、客户端的简单示例
WebSocket 的用法相当简单。
下面是一个网页脚本的例子（点击这里看运行结果），基本上一眼就能明白。
var ws = new WebSocket("wss://echo.websocket.org");

ws.onopen = function(evt) { 
  console.log("Connection open ..."); 
  ws.send("Hello WebSockets!");};

ws.onmessage = function(evt) {
  console.log( "Received Message: " + evt.data);
  ws.close();};

ws.onclose = function(evt) {
  console.log("Connection closed.");}; 

六、WebSocketd
下面，我要推荐一款非常特别的 WebSocket 服务器：Websocketd。
它的最大特点，就是后台脚本不限语言，标准输入（stdin）就是 WebSocket 的输入，标准输出（stdout）就是 WebSocket 的输出。

WebSocket 教程 - 阮一峰的网络日志.html
java 实现websocket的两种方式 - 锐洋智能 - 博客园.html
Java后端WebSocket的Tomcat实现 - 孤傲苍狼 - 博客园.html
