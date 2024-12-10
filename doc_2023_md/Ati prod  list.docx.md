Ati prod  list



Bot tlgrm recv
C:\在修改的内容\gamebot\jbbot\tlgrm\keywoHdlr.js

Betstr format convert
Log tool 
 C:\在修改的内容\gamebot\jbbot\lib\logx.php
C:\modyfing\jbbot\lib\log23.php

Dbg tool php

C:\modyfing\jbbot\lib\dbg_consl.php

For console,ang log dbg stp dbg




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


 Aurto load lib fun
C:\modyfing\jbbot\lib\iniAutoload.php


ob_start();

require_once __DIR__."/iniErrCathr.php";
//  require_once __DIR__ . "/lotrySscV2.php";
require_once __DIR__."/../app/common/betstr.php";
//------------------auto load functions
$dirs307='/../../lib/,/../lib/,/lib/,/';
$arr_dirs=explode(",",$dirs307);
$libnames="ex,json,kaijx,logx,ltrx,str,strcls,strx,tlgrmV2,betstr,encodex,lotrySscV2,log23";
$arr_libs307=explode(",",$libnames);

foreach ($arr_dirs as $dir) {
   foreach ($arr_libs307 as $libnm) {

       $fname=__DIR__.$dir. $libnm . '.php';
       if(file_exists( $fname))
       {
           require_once  $fname;
       }

   }
}
ob_end_clean();


Msghdlr mapHdlr
Msg>> msg.php
Msg>> msg covnert>> msg.php

Tlgrm lib warp again
timer
C:\在修改的内容\gamebot\jbbot\lib\timer.php

Json.php   supt cn n pretty


Ref
Prgrm impt fun  code samp

