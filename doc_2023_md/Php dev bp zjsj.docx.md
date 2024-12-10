Php dev bp zjsj 


Env tool  phostudy
Easy install ext already have.
N rds tool all in one ..
Mggodb tool ..good 
sqlite


Dbg  tool   phpstorm
Zend studio ，phpeclipse
Vscode cant dbg
Cli dbg file  phpdbg ext

Xdbg also need,var dump can show linenum
Dev method
Just as fp and block prgrm..dont oo

合理命名变量
Fun name just    namespcname__fun...
Strx__split() just is good naming..
Nmspc fornt ,an d bouble xiahwasye..
Data map...sprt data n code
Ur api just dsl

查看次语言的bug和要避免的坑


语言与sdk bug
浮点运算时应注意丢失精度  使用增强lib
(PHP遵循IEEE 754双精度)

Mb字符串问题   汉字操作，不要使用默认的有bug
正则表达式使用u  实现汉字操作

IDE SETTING
Left file nav,rig is fun outline nav
Set line height num can showmore line 50 line
Double screen is better
Win11 swtitch desktop also good

Ex catch  set all glb ex cathr 
Reg ex cathr mode vs trycatch mode
用@屏蔽错误消息
If 需要稳定性
function  loadErrHdr()
{
   global $errdir;
   $errdir=__DIR__."/../runtime/";
   $GLOBALS['$errdir']=$errdir;


 //  require_once __DIR__."/../lib/logx.php";

   ini_set('display_errors', 'on');
   error_reporting(E_ALL ^ (E_NOTICE | E_WARNING));
   ini_set("log_errors", 1);
   ini_set("error_log", $errdir . date('Y-m-d H') . "lg142_errLog.txt");


   set_error_handler("error_handler142");
   register_shutdown_function('shutdown_hdlr');

   set_exception_handler('ex_hdlr');


}


Log api ur logx is better
Maybe use in ur lib..so not load tp frmwk..

Log bp .... output var n vavlue
Target file just as lev is ok..
Dync method as targetfile is good

Chougon use phpstom is beter
Work with other lan...js also better together 
Easy dbg..

Release resouce juse use exec systemis bettr
hotboot
