Prgrm impt fun  solu code samp v2 x820




Save echo to log file
Use ob lib
Clr output at echo ..for recv json
Use ob lib

Dbg not delete dump 
Use ob

Stp deb brek..use dbg tool 
Get loc vars and die()   show to console and log

Set globale err catcher

C:\modyfing\jbbot - 副本 (4)\lib\iniErrCathr.php

Tp ex catch
class ExceptionHandle extends Handle
{
    /**
     * 不需要记录信息（日志）的异常类列表
     * @var array
     */
 
    /**
     * 记录异常信息（包括日志或者其它方式记录）
     *
     * @access public
     * @param  Throwable $exception
     * @return void
     */
    public function report(Throwable $exception): void
    {
        // 使用内置的方式记录异常日志
        parent::report($exception);
        $errdir="";
        $j=json_encode($exception,JSON_UNESCAPED_UNICODE|JSON_PRETTY_PRINT);
      //  $lineNumStr = "  " . __FILE__ . ":" . __LINE__ . " f:" . __FUNCTION__ . " m:" . __METHOD__ . "  ";
      //  \think\facade\Log::error(  $lineNumStr);

      $lineNumStr = " m:" . __METHOD__ . "  " . __FILE__ . ":" . __LINE__    . PHP_EOL;

      \think\facade\Log::error("------------- $lineNumStr -------------------------");
        \think\facade\Log::error("----------------errrrrx_tp_ex_cathr---------------------------");
        \think\facade\Log::error("file_linenum:".$exception->getFile().":".$exception->getLine());
        \think\facade\Log::error("errmsg:".$exception->getMessage());
     //   \think\facade\Log::error("errtrace:".$exception->getTrace());
        \think\facade\Log::error("errtraceStr:".$exception->getTraceAsString());
        \think\facade\Log::error("----------------errrrr finish---------------------------");

       // file_put_contents( $errdir.date('Y-m-d H')."ex648_exhdlRpt.txt", $exception->getMessage() .PHP_EOL, FILE_APPEND);
      //  file_put_contents( $errdir.date('Y-m-d H')."ex648_exhdlRpt.txt",  $j.PHP_EOL, FILE_APPEND);
        var_dump($exception->getMessage().$exception->getFile().":".$exception->getLine());
        var_dump($exception->getTraceAsString());
        
        throw  $exception;
    }

Autoload clas


spl_autoload_register(function ($class_name ) {
   // var_dump($class_name);  //"ltrx"
   ob_start();
   if(file_exists(__DIR__."/../../lib/". $class_name . '.php'))
       require_once __DIR__."/../../lib/". $class_name . '.php';

   else if(file_exists(__DIR__."/../lib/". $class_name . '.php'))
       require_once __DIR__."/../lib/". $class_name . '.php';
   else if(file_exists(__DIR__."/lib/". $class_name . '.php'))
       require_once __DIR__."/lib/". $class_name . '.php';
   else if(file_exists(__DIR__."/". $class_name . '.php'))
       require_once __DIR__."/". $class_name . '.php';

       ob_end_clean();

});


Markdown txt encode


replace_markdown()


Php hilev exec code fun  exec system
Dyna exec code eval
Json encode supt chchar

Hotboot throw system exec

Timer task
Dync fun method for log lev

__callStatic()，用静态方式中调用一个不可访问方法时调用

Cfg fun
Use option mode first..then cfgfile moshi ..
如果cfg选项很多，可以使用cfgfile指定模式
采用多配置文件模式，命令行指定，或者启动文件来指定

自己实现命名空间的实现

Ref
Ati prod  list

