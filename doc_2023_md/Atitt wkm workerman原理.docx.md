Atitt wkm workerman原理


Workerman是一个高性能的PHP Socket服务器框架。它采用了多进程+多线程的设计模式，可以处理大量并发连接。
Workerman底层使用了C++语言写的异步事件驱动的高性能Web服务器框架libevent，通过在上面封装了PHP语言接口，使得PHP开发者可以方便地编写高性能的Socket服务端。
Workerman还支持多协议，包括HTTP、Websocket、TCP等，可以方便地搭建即时通讯、游戏、物联网等需要高并发的在线应用。

