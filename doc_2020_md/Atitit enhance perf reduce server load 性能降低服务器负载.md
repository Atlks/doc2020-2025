Atitit enhance perf reduce server load 性能降低服务器负载

统计哪个进程占有资源较多

 ps -ef > xx.log
然后note pad查找 grpby


Look task count  cpu,mem,io,net
烧掉某个java 进程 by name
  ps -ef | grep TonzhiJinxinzhongList | grep -v grep   | awk '{print $2}' | xargs kill -9






定时gc

xargs kill -9

启动增加outtime 时间秒
		//must exit bcz tonzhi wss not  gc
		int timetout = Integer.parseInt(args[0].trim());
		Util.timeOutExitRuntime(timetout*1000);
批量gc xargs kill -9

查找大文件日志
