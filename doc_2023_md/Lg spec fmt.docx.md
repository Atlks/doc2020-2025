Lg spec fmt


程序基本结构就是函数和参数

函数和返回值使用》》》和<<< 和标注
函数直接分隔使用双回车换行符。。
调用方法和参数按照源码模式数出来  》》》  fun xxx(((  args )))
返回值    《<< timestmp funname  ret:xxxx
里面的变量输出  timestmp funname   xxx=>var 格式

Invoke

log_enterMethV2(__METHOD__,func_get_args(), $GLOBALS['lgnm307']);

function log_Vardump(


log_vardumpRetval(__METHOD__,$text, $GLOBALS['lgnm307']);



1207171911 [app\controller\HandleLhc::processMessage] reply_text=>【十 jarkas 大鱼 刘洋 汤姆-879006550】



1207171911 !>>FUN app\controller\HandleLhc::processMessage((( [{"message_id":50,"from":{"id":879006550,"is_bot":false,"first_name":"十 jarkas 大鱼 刘洋 汤姆","username":"Xxx0079468","language_code":"en"},"chat":{"id":-4038077884,"title":"msgNode","type":"group","all_members_are_administrators":true},"date":1701940750,"text":"Z9"}] )))


1207171911 !>>FUN app\common\Game2handlrLogicLhc::regex_betV2((( ["Z9"] )))
1207171911 <<<<< [app\common\Game2handlrLogicLhc::regex_betV2] <<<ret:【十 jarkas 大鱼 刘洋 汤姆-879006550】






