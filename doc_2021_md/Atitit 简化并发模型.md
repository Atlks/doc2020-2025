Atitit 简化并发模型


常，我们写服务器处理模型的程序时，有以下几种模型：
（1）每收到一个请求，创建一个新的进程，来处理该请求；
（2）每收到一个请求，创建一个新的线程，来处理该请求；
（3）每收到一个请求，放入一个事件列表，让主进程通过非阻塞I/O方式来处理请求
上面的几种方式，各有千秋，
第（1）中方法，由于创建新的进程的开销比较大，所以，会导致服务器性能比较差,但实现比较简单。
第（2）种方式，由于要涉及到线程的同步，有可能会面临死锁等问题。
第（3）种方式，在写应用程序代码时，逻辑比前面两种都复杂。
综合考虑各方面因素，一般普遍认为第（3）种方式是大多数网络服务器采用的方式
