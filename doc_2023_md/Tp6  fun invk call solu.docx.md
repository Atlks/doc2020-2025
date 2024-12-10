Tp6  fun invk call solu



传递参数使用global参数，返回值要是有回调模式ret val need callback mode ..bcz invk tp is last cmd php code 

Test

<<?php

//tp6  cmd test
//  php.exe  test\call_tp_t.php calltp
//echo 111;
// 命令行入口文件
// 加载基础文件
require __DIR__ . '/../vendor/autoload.php';

//$fun = "fff641";

$GLOBALS['fun641'] = "fff641";
$GLOBALS['prm641'] = ["ttt65222__PRM"];
$GLOBALS['callbackFun'] =function ($ret){
 echo  $GLOBALS['ret641'];
 echo 99;
};



// 应用初始化
(new \think\App())->console->run();


function fff641($prm) {
 echo $prm;
 return "retval111";
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

