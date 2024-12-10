Php  dbg 总结



打开dbg ，tp调试模式

要回显记录哪些信息
方法参数，文件名和linenum
Sql

Console测试法，，
只需要var dmp 日志即可。。Ex会自动抛出print



日志法
全面记录  行号 方法名称和参数 魔术变量

 $lineNumStr =  __METHOD__ . json_encode(func_get_args()) . "  " . __FILE__ . ":" . __LINE__ . " f:" . __FUNCTION__;
    //$logtxt = " dwijyo() betnumL:" . $betContext . "  kaijnum:" . $kaij_num  . $lineNumStr;

    log_info($lineNumStr);


全面记录ex
  $j = json_encode($exception, JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT);
    log_err("----------------errrrr---------------------------");
    log_err("errmsg:" . $exception->getMessage());
    log_err("file_linenum:" . $exception->getFile() . ":" . $exception->getLine());

    //   \think\facade\Log::error("errtrace:".$exception->getTrace());
    log_err("errtraceStr:" . $exception->getTraceAsString());
    log_err("----------------errrrr finish---------------------------");


可以注册全局狗子记录ex

