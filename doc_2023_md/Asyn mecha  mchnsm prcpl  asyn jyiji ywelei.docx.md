Asyn mecha  mchnsm prcpl  asyn jyiji ywelei


One theard bg yg nextfun  invik task  feodg yg dijeo...zo zole...


Zaiyige dif d thread zo pickup invk....continue...zo ok..


Async time php





function swoole_timer_afterx($fun, $args, $delaytime_sec)
{
   $get_included_files553 = get_included_files();
   require_once __DIR__ . "/../../lib/iniAutoload.php";
   $get_included_files553 = get_included_files();
    require_once __DIR__ . "/../../lib/file.php";
   log23::Timerinfo(__LINE__.__METHOD__, "args", json_encode(func_get_args(), JSON_UNESCAPED_UNICODE));


   $exeTime = $delaytime_sec + time();

   $nextFuncIvkTxt = asyn_build_async_task($fun, $args, $exeTime);
   $fil = sprintf("%s/../../pushmsg/%s_%s.txt", __DIR__, time(), rand());
   file_put_contentsx($fil, $nextFuncIvkTxt);


}

function asyn_build_async_task($fun, mixed $arg1214, int $exeTime)
{
   log23::Timerinfo(__LINE__.__METHOD__, "args", json_encode(func_get_args(), JSON_UNESCAPED_UNICODE));

   $obj = array("fun" => $fun, "args" => $arg1214, "exeTime" => $exeTime, "crt_time" => date("Y-m-d his"));
   $nextFuncIvkTxt = json_encode($obj, JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT);
   return $nextFuncIvkTxt;
}


function async_timer_start()
{

   require_once __DIR__ . "/../../lib/iniAutoload.php";
   log23::Timerinfo(__METHOD__, "args", json_encode(func_get_args(), JSON_UNESCAPED_UNICODE));


   try {
       $dir = sprintf("%s/../../pushmsg/", __DIR__);

       $list = scandir($dir);
//ob_start();
       var_dump($list);
       log23::Timerinfo(__METHOD__, "filelist", json_encode($list, JSON_UNESCAPED_UNICODE));

       $a = [];
       foreach ($list as $fil_basename):

           if (basename($fil_basename) == ".gitkeep" || basename($fil_basename) == "." || basename($fil_basename) == "..")
               continue;
           if ($fil_basename == "oked")
               continue;

           call_user_func_arrayx("asyn_item_task_process", array($fil_basename));
           // item_task_process($fil_basename);

       endforeach;
   } catch (\Exception $exception) {

       var_dump($exception);
       log23::Timererr(__METHOD__, "", __METHOD__ . json_encode(func_get_args(), JSON_UNESCAPED_UNICODE));
       log23::Timererr(__METHOD__, "e", $exception);

   }
   var_dump(11);


}


function asyn_item_task_process($fil_basename)
{
   $allIncFile = get_included_files();
   require __DIR__ . "/../../lib/iniAutoload.php";
   $allIncFile = get_included_files();
   require_once __DIR__ . "/../../lib/file.php";
   require_once __DIR__ . "/../../lib/str.php";
   require_once __DIR__ . "/../../lib/fun.php";

   $dir = sprintf("%s/../../pushmsg/", __DIR__);



       $filpath = sprintf("%s%s", $dir, $fil_basename);
       $txt = file_get_contents($filpath);


       $task = json_decode($txt, true);
       $exe_tmstp = $task['exeTime'];


       if (time() > $exe_tmstp) {
           //move to oked mq
           $taskFinishDir = sprintf("%soked/", $dir);
           file_mov($filpath, $taskFinishDir);

           log23::Timerinfo(__METHOD__, "****************redy to exe,rd txt=>" . $txt);
           var_dump($fil_basename);
           var_dump($txt);
           $funx = $task['fun'];
           $fun123 = str_parseToFunExprs($funx);
           $args = $task['args'];
           call_user_func_arrayx($fun123, $args);
           // $cls->$meth($task);
       }



}

