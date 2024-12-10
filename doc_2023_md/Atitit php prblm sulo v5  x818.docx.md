Atitit php prblm


Def mlt nmspc in one file

Namespace afadf{}
namespace {
}
Cfg file define..use -c param  

--ini  show cfg file path


C:\Users\ati>D:\wamp\bin\php\php7.1.9\php.exe  -c   D:\wamp\bin\apache\apache2.4
.27\bin --ini
Configuration File (php.ini) Path: C:\Windows
Loaded Configuration File:         D:\wamp\bin\apache\apache2.4.27\bin\php.ini
Scan for additional .ini files in: (none)
Additional .ini files parsed:      (none)

不显示错误
调整框架debug模式。。
error_reporting(E_ALL);


不显示任何错误，一运行自动推出
原来是某个文件语法错，单不知为什么会不提示。。
或者循环依赖了可能。。
