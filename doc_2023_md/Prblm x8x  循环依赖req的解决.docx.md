Prblm x8x  循环依赖req的解决

使用 global var   知名上一个ref文件名即可。。



$GLOBALS['refLib419']='betstr';
require __DIR__ . "/../../lib/iniAutoload.php";


这里必须是require，因为要每次要重新加载。。不如一次忽略就永远忽略了


$libnames="ex,json,kaijx,logx,ltrx,str,strcls,strx,tlgrmV2,betstr,encodex,lotrySscV2,log23";
$arr_libs307=explode(",",$libnames);


$key = array_search($GLOBALS['refLib419'], $arr_libs307);
if ($key !== false) {
   unset($arr_libs307[$key]);
}

