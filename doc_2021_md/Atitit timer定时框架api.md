Atitit timer定时框架api

C:\wamp\bin\php\php7.1.9\php.exe C:\Users\ATI\PhpstormProjects\apiprj\tmrRefrsParam.php task2.php 1


  [0] => C:\Users\ATI\PhpstormProjects\apiprj\tmrRefrsParam.php
    [1] => task2.php
[2] => 1

指明定时运行的任务脚本，以及定时时间。。。

只能命令行执行。。Phpstorm里面执行报错会。。

<?php

//  C:\wamp\bin\php\php7.1.9\php.exe  C:\Users\ATI\PhpstormProjects\apiprj\tmrRefrsParam.php -t 1 -b task2.php
//  Workerman version:3.5.25          PHP version:5.6.31

require_once(__DIR__ . '/Workerman/Autoloader.php');  //. 
require_once "conn.php";


use Workerman\Worker;
use Workerman\Lib\Timer;

echo "接收到{$argc}个参数";
print_r($argv);
$taskfile=$argv[1];
$time_interval=(int)$argv[2];
//-----------------tier
$task = new Worker();

$task->onWorkerStart = function ($task) {

  global  $time_interval;
    $timer_id = Timer::add($time_interval,
        function () {
            global $taskfile;
            echo $taskfile;
           require( $taskfile);  //req file task
            // echo time()."123\r\n";

        }

    );

};

// 运行所有workers

Worker::runAll();

