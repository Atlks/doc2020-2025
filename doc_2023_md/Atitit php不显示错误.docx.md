Atitit php不显示错误


[PHP] PHP在CLI环境下的错误日志
 原创
大灰狼小红帽2021-06-17 19:12:29©著作权
文章标签PHP文章分类PHP后端开发阅读数1103
1.
display_errors = Off;//控制php是否输出错误;在生产环境中输出会泄露敏感信息;建议记录错误而不是将它们发送到STDOUT
off :不显示任何错误;stderr :向STDERR显示错误(仅影响CGI/CLI) ;On/stdout :向STDOUT显示错误(就是直接在屏幕打印错误)
2.
log_errors = On ;//将错误记录到服务器指定的日志;STDERR ; 或者error_log指令指定的位置
3.
error_log = /var/log/php_errors.log ;//错误日志指定位置
比如php代码:

直接在屏幕打印出错误,如果不开启display_errors,就不会显示

error_log指定的错误日志中也会显示

