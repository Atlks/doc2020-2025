Atitt 异步实现的俩种方式



#最简单多进程线程模式   Sleep+单个进程模式

InvokeTimer( sleep8sec(task))

这个的本智是吧task队列放在了os中，利用os的定时调度去执行


#单进程模式 定时检测任务task队列去处理
使用mysql的timer去调整sleep的时间，同意减一，每秒
自己写个os的定时task处理调度。。去执行

改进定的单进程模式，fork子进程避免阻塞



# 混合模式   
