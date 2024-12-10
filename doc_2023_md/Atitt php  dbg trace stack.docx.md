Atitt php  dbg trace stack



某个方法传入的参数出错，需要知道上一级调用方法和invoke链
在方法里面增加调用链日志跟踪


    $log_txt=__METHOD__. json_encode( func_get_args());
      
        \think\facade\Log::debug (  $log_txt);

        \think\facade\Log::debug ( debug_backtrace());


debug_zval_dump



LOG info输出丢失问题

多加几个
   $t = $this->http_helper->http_request($url);
              \think\facade\Log::info($t);
              \think\facade\Log::debug($t);
              \think\facade\Log::notice($t);

