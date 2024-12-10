Atitit dbg 方法总结

除了日志文件，，还可以使用零食存储session来存放数据。。

error_log('$response:'.$response."\r\n",3, $logfile79);
error_log( $response."\r\n",3, $logfile79);
file_put_contents($logfile712, '$response:'.$response."\r\n", FILE_APPEND );
error_log('$response:'.$response."\r\n");
//var_dump($dbgInvokeChain);

$_SESSION['$response']=$response;

