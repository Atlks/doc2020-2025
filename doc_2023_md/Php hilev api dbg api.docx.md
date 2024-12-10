Php hilev api dbg api   15条


Ex fun  ,and log fun









Error的处理 Exception

error_reporting(E_ALL ^ (E_NOTICE | E_WARNING));

error_log 
set_error_handler('error_handler142');  //this only for log dbg ,,,if local dbg ,,console dbg is more easy
register_shutdown_function('shutdown_hdlr');
set_exception_handler('ex_hdlr');

Exception的行号 ，消息，堆栈
restore_exception_handler — 恢复之前定义过的异常处理函数。
名 trigger_error

error_clear_last — 清除最近一次错误
error_get_last — 获取最后发生的错误
error_log — 发送错误信息到某个地方
reset_error_handler — 设置用户自定义的错误处理函数
error_reporting — 设置应该报告何种 PHP 错误
restore_error_handler — 还原之前的错误处理函数
trigger_error — 产生一个用户级别的 error/warning/notice 信息
user_error — 别



set_exception_handler — 设置用户自定义的异常处理函数


 \think\facade\Log::error("file_linenum:".$exception->getFile().":".$exception->getLine());
        \think\facade\Log::error("errmsg:".$exception->getMessage());
     //   \think\facade\Log::error("errtrace:".$exception->getTrace());
        \think\facade\Log::error("errtraceStr:".$exception->getTraceAsString());


捕获堆栈查看
debug_backtrace — 产生一条回溯跟踪(backtrace)
debug_print_backtrace — 打印一条回溯。
__method__ 当前方法
func_get_args()   当前方法参数



查看变量

Var_dump
Print_r


中断流程

Die()
Exit()

日志记录api
Error_log
file_put_contents



具体而言error_log('test', 3, 'test.txt')，文档中的内容（ file_put_contents和error_logfile_put_contents('test.txt', 'test', FILE_APPEND) ）没有区别，因为两者都只是将其附加到文件中。
这些函数之间的主要区别在于，如果您设置 、或 ，则error_log它们不仅可以记录到文件，还可以发送到 PHP 的系统记录器、将错误作为电子邮件发送或将其发送到 SAPI 日志处理程序。014
使用file_put_contents确实允许指定字符串、数组或流资源，而error_log仅允许指定字符串作为消息。这可能会产生影响，具体取决于您想要记录的数据，但是您的示例只是一个字符串，因此它没有任何重要性。

