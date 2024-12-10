Tp6  fun invk call solu v2



main

<?php

//tp6  cmd test
//  php.exe  test\call_tp_t.php calltp


use app\model\Setting;

require_once __DIR__."/../lib/sys1011.php";



function main101() {
//  echo 999;

 $set = Setting::find(3);
 echo   $set->value;

// return "retval111";
}






// call main（）
call_inTpX("main101");


Sys.php call_inTpX


<?php



function call_inTpX(string $f ) {

 require __DIR__ . '/../vendor/autoload.php';


 $GLOBALS['fun641'] = $f;
 $GLOBALS['prm641'] = [];
 $GLOBALS['callbackFun'] = function (){};

 // 应用初始化
 (new \think\App())->console->run();
}


Config/copnsole.php  add cmd   'calltp'to calltp.PHP


<?php

require_once __DIR__."/../app/calltp.php";
// +----------------------------------------------------------------------
// | 控制台配置
// +----------------------------------------------------------------------
return [
   // 指令定义
   'commands' => [
          'calltp'=>'\calltp'
       
   ],
];


class calltp


<?php
use think\console\Command;
use think\console\Input;
use think\console\Output;

class calltp extends Command
{
 protected function configure()
 {
   $this->setName('calltp')->setDescription('Here is the remark ');
 }

 protected function execute(Input $input, Output $output)
 {
       //$output->writeln("TestCommand:");
  $ret=     call_user_func_array($GLOBALS['fun641'],$GLOBALS['prm641']);

   $GLOBALS['ret641']=$ret;
if ($GLOBALS['callbackFun'])
 $GLOBALS['callbackFun']($ret);

 }
}






