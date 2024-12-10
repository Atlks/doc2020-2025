Websockt php


PHP 实现 websocket 服务器
PHP 实现 websocket 的话，主要是应用 PHP 的 socket 函数库：
PHP 的 socket 函数库跟 C 语言的 socket 函数非常类似，以前翻过一遍 APUE, 所以觉得还挺好理解。在 PHP 手册中看一遍 socket 函数，我想大家也能对 php 的 socket 编程有一定的认识。
下面会在代码中对所用函数进行简单的注释

下载安装Workerman
复制到主要目录即可
服务端
C:\wamp\www\ws\ws_serv.php

<?php

 
use Workerman\Worker;
require_once __DIR__ . '/../Workerman/Autoloader.php';

// 注意：这里与上个例子不同，使用的是websocket协议
$ws_worker = new Worker("websocket://0.0.0.0:1314");

// 启动4个进程对外提供服务
$ws_worker->count = 4;

// 当收到客户端发来的数据后返回hello $data给客户端
$ws_worker->onMessage = function ($connection, $data) {
    // 向客户端发送hello $data
    $connection->send('hello ' . $data);
};

// 运行worker
Worker::runAll();


启动 服务端

命令行运行
php ws_test.php start


----------------------- WORKERMAN ----------------------------- 
Workerman version:3.5.25 PHP version:5.6.31 ------------------------ WORKERS ------------------------------- worker listen processes status none websocket://0.0.0.0:1314 4 [ok]



客户端连接

测试
打开chrome浏览器，按F12打开调试控制台，在Console一栏输入(或者把下面代码放入到html页面用js运行)
// 假设服务端ip为127.0.0.1
ws = new WebSocket("ws://127.0.0.1:2000");
ws.onopen = function() {
    alert("连接成功");
    ws.send('tom');
    alert("给服务端发送一个字符串：tom");};
ws.onmessage = function(e) {
    alert("收到服务端的消息：" + e.data);};
注意：
1、如果出现无法访问的情况，请参照手册常见问题-连接失败一节排查。
2、服务端是websocket协议，只能用websocket协议通讯，用http等其它协议无法直接通讯。

swoole太麻烦

Ref
Atitit websocket 的前后端实现最佳实践t66

目录
1. 技术选型	1
2. 1.首先，在pom.xml引入如下jar包。Java-WebSocket-1.3.0.jar	1
3. 后端WsServer	1
4. 在线测试古巨基	5

Atitit websocket 使用大概总结
六、WebSocketd
下面，我要推荐一款非常特别的 WebSocket 服务器：Websocketd。
