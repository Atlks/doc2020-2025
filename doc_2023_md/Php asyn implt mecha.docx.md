Php asyn implt mecha 


$nextFunc="\app\controller\logic.nextFun";

require_once __DIR__."/../common/asyn_timer.php";
swoole_timer_afterx( $nextFunc,array($id,$sign),$delay_time / 1000);


Naming just ref   famous sdk name is ok... easy to search dat..



Timer  start just this
\async_timer_start();

