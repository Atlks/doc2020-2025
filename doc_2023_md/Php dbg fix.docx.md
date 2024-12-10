Php dbg fix


十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:52 am]
dbg art bk

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:53 am]
dbg tech 。。。console调试
log dbg。。获取相关信息 行号 文件名 函数名 类名方法名  出错信息  调用Stack Overflow

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:54 am]
全部ex捕获 钩子

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:54 am]
getlasterr

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:57 am]
断点调试 log dbg, console dbg,,remore debug

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:58 am]
api dbg http psot tool

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 4:58 am]
dbg sdk open

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:00 am]
tp log looktool...php rd log output...use url look..rmt dbg log

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:01 am]
rmt log

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:01 am]
日志就是控制台的持久化

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:02 am]
可以使用多屏显示控制台输出哇。use CP

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:03 am]
bardumpdie()和exit()
die()和exit()函数都有终止线程的作用，是php断点调试需要使用的最主要的函数，它们也是php程序员使用非常频繁的函数。然而两者又有什么区别呢？在程序调试时需要注意什么问题

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:04 am]
die()函数一般与“or”一并使用，写作“or die()”，经常看到这样的语句：

$file = fopen($filename, 'r') or die("抱歉，无法打开: $filename")

or在这里是这样理解的，因为在PHP中并不区分数据类型，所以$file既可以是int也可以bool，所以这样的语句不会报错。但其处理过程

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:04 am]
php手册对两者的解释如是说：
exit() 函数输出一条消息，并退出当前脚本。该函数是 die() 函数的别名。
die() 函数输出一条消息，并退出当前脚本。该函数是 exit() 函数的别名

十 jarkas 大鱼 刘洋 汤姆, [06/08/2023 5:05 am]
debug_print_backtrace

debug_print_backtrace — 打印一条回溯。输出类似如下：

1
#0  c() called at [/tmp/include.php:10]
2
#1  b() called at [/tmp/include.php:6]
3
#2  a() called at [/tmp/include.php:17]
4
#3  include(/tmp/include.php) called at [/tmp/test.php:3]
7. debug_backtrace

产生一条 PHP 的回溯跟踪(backtrace)，返回一个包含众多关联数组的 array。返回结果
