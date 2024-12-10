Php simple solu ..cmd mode smpl php sytanx


Norml stamt

substr  abcdef  2
Retval just store to glb var is bettr..


Fun def



解析器 parser


var_dump(dsl__callFunCmdMode("substr  abcdef  2"));
function dsl__callFunCmdMode($cmd)
{
 include_once __DIR__."/iniAutoload.php";
 $arr= explode(" ",$cmd);
 $arr= array_filter($arr);
$fun= $arr[0];



 $arr_args=array_slice($arr,1);
 //$arr_args[1]=3;
 include_once __DIR__."/iniAutoload.php";
 // xdebug_call_function()
 return call_user_func_arrayx($fun, $arr_args);
}

