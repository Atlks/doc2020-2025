Atipro sample doc dbg tool 


<?php
$a = 1;
$aa = 2;
$aa2 = 222;

require_once __DIR__ . "/dbg_consl.php";
function f1($prm_trson_into_fun)
{
   $varInFun = 99;


   $varInFun = 100;
   breakStopHere(__METHOD__,func_get_args(), __LINE__, get_defined_vars(),__FILE__);
   echo $prm_trson_into_fun;
}

f1(664);


function breakStopHere($funname,$fun_args,$line,$vars_arr,$fil)
{
 ob_start();
   echo $funname."(".json_encode($fun_args,JSON_UNESCAPED_UNICODE) .") ".$fil.":". $line."\r\n";
  $var_loc1=11;
 //  $vars_arr = get_defined_vars();
   file_put_contents( "j634.json",json_encode($vars_arr ) );
//var_dump($vars_arr);


   $vars_arr_tojson=json_decode(  json_encode($vars_arr));

   $arr_loc=[];
   foreach ($vars_arr_tojson as $key => $value) {
       if (!str_starts_with ($key, "_"))
       {
           $arr_loc[$key]=$value;
           echo "$key=>$value\n";
       }

   }

   var_dump($arr_loc);
   $info=ob_get_contents();
   ob_end_flush(); //show scr
    file_put_contents("out727.txt.log",$info.PHP_EOL,FILE_APPEND);

   die();

}




C:\phpstudy_pro\Extensions\php\php8.0.2nts\php.exe C:\modyfing\jbbot\lib\dbg_sampl.php
f1([664]) C:\modyfing\jbbot\lib\dbg_sampl.php:13
prm_trson_into_fun=>664
varInFun=>100
C:\modyfing\jbbot\lib\dbg_consl.php:31:
array(2) {
  'prm_trson_into_fun' =>
  int(664)
  'varInFun' =>
  int(100)
}

Process finished with exit code 0

