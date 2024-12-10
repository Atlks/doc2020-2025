Php async 异步实现方式


使用evet loop来循环。。



每个task( nextExecTime ,taskname,durtime)


主循环每次对比任务的nextexetime,如果到了，则充值nextexetime=nextexetime+durtime
并执行task代码


多线程模式可以使用sleep（durtime) 来实现 
