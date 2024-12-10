HTTP 400 错误

原因，参数没有urlencode。。编码后就ok了。。

$endTime = date("Y-m-d H:i:s");
$endTime=urlencode($endTime);
$url = "http://localhost:89/api.php?call=kaijVd_outputFile%20$sec,$endTime";
var_dump($url);
$f=file_get_contents(  $url  );



