Log spec


Msg fmt time [Line.meth] var=>valobj
Time ***line.fun[args]
Time  [Line.meth]  msg
Log info
Enter method       log    $fun,$args
普通变量日志   log   __line.fun  var  obj
Fun ret   >>   log __line.fun  ret  obj
Normal msg >>  log __line.fun   msgx



Per impt dsl biz fun need log
Can auto callFun to log    funname(args)   n ret val..//

log_enterMeth_reqchain(__METHOD__,func_get_args());

"isWebhkRecv"]] ret=>FALSE 

http url sql cmd

流程控制在日志上的显示  for ifelse等
貌似只能在for 开头和结尾>>>> foreach

>>>>>for end
中间太多了，设置padding太麻烦
分级日志，，，fun+reqid是个不错的模式
日志按照功能来分类目录
，每次请求一个日志文件，方便分析排查
Bot的话每次一个msg作为请求记录
Err和wanning单独显示在前面
普通日志写在功能文件夹里面去方便，查看，不影响err的查看优先级
