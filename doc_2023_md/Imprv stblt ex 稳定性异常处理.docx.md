Imprv stblt ex 稳定性异常处理


Biz api里面处理biz ex 方便找出问题。。


全局windows异常注册
Jq异常注册
Vue异常
Jq捕获异常


$.get($url, function (data) {
   console.log("[http_get_jqget] ret=>" + $url)
   log_info(" [jqGet] ret=>" + data);
   f(data)
}).fail(function (jqXHR, textStatus, errorThrown) {
   let arg = JSON.stringify(arguments);
   alert("参数错误 "+   JSON.stringify(  jqXHR. responseJSON.errors));
   log_err(arg)
});

