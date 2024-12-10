Atitt php timer async异步定时的实现


Timer  timerstat

把任务持久化到磁盘，然后队列，移动，执行


另外一个timer只是个内存timer，每次可以执行，貌似这个更加简单。。。


单另外一个更加文档，因为支持热更新，以及资源自动释放，防止dbconn沾满
