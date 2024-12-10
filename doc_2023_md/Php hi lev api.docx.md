Php hi lev api



Eval 动态执行
Console dbg var dump
Err 错误处理 于错误日志

   trigger_error("变量值必须小于等于 1");



ini_set('display_errors', 'on');
//error_reporting(E_ALL);
error_reporting(E_ALL ^(E_NOTICE | E_WARNING)); 
ini_set("log_errors", 1);
ini_set("error_log", $errdir.date('Y-m-d H')."lg142_errLog.txt");



set_error_handler('error_handler142');  //this only for log dbg ,,,if local dbg ,,console dbg is more easy
register_shutdown_function('shutdown_hdlr');
//set_Exception_handler();
set_exception_handler('think\ex_hdlr');
set_error_handler("think\\error_handler142");
register_shutdown_function('think\shutdown_hdlr');




日常日志模式

 $lineNumStr =  __METHOD__ . json_encode(func_get_args()) . "  " . __FILE__ . ":" . __LINE__ . " f:" . __FUNCTION__;
    //$logtxt = " dwijyo() betnumL:" . $betContext . "  kaijnum:" . $kaij_num  . $lineNumStr;

    log_info($lineNumStr);

