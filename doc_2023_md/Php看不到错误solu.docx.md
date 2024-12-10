Php看不到错误solu


现代语言  错误及异常模式总结



错误及异常


php把用户触发的错误为ex模式 ，这和c++有点类似，


打开错误显示模式

ini_set('display_startup_errors', 'on');
ini_set('display_errors', 'on');
error_reporting( E_ALL & ~E_NOTICE);
ini_set("log_errors", 1);
ini_set("error_log", $errdir.date('Y-m-d H')."error_log236_55808.txt");
set_error_handler
register_shutdown_function
打开框架的debug模式

