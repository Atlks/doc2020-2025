Phpdbg useage



数介绍

phpdbg是php的一个sapi，它可以以命令行的方式调试php。常用参数如下：

The following switches are implemented (just like cli SAPI):
-n ignore php ini
-c search for php ini in path
-z load zend extension
-d define php ini entry
The following switches change the default behaviour of phpdbg:
-v disables quietness
-s enabled stepping
-e sets execution context
-b boring - disables use of colour on the console
-I ignore .phpdbginit (default init file)
-i override .phpgdbinit location (implies -I)
-O set oplog output file
-q do not print banner on startup
-r jump straight to run
-E enable step through eval()





要想加载要调试的php脚本，只需要执行exec命令即可。如下：
#phpdbg......
prompt> exec ./test_phpdbg.php
当然我们也可以在启动phpdbg的时候，指定e参数。如下：
#phpdbg -e ./test_phpdbg.php

可以在当前 phpdbg 环境中使用 e 命令指定文件进行载入，也可以在运行 phpdbg 的时候通过 -e 来指定需要载入的文件

To load the PHP script you want to debug, just execute the EXEC command. As follows:

Set breakpoint

2. 设置断点
最简单的设置断点方法 b + 行号L (在当前文件L行设置一个断点，b是break缩写)
⚠️断点行不能是空行
prompt> b 17
[Breakpoint #0 added at /data0/www/htdocs/api.life.lianjia.com/cli/cli.php:17]



List breakponikt
查看断点 和gdb一样，phpdbg也是使用info break命令查看断点。示例如下：
....
prompt> info break
删除断点  break del 命令
和gdb命令不一样。phpdbg的删除断点不是delete命令，而是break del 命令。示例如下：
......
prompt> break del 1[Deleted breakpoint #1]
prompt>......

  clear     clear one or all breakpoints


prompt> info v
[Variables in C:\modyfing\jbbot\app\common\asyn_timer_tpCmd.php (6)]
Address            Refs    Type      Variable
0x1abcf460580      1       array     $argv
0x1abcf4605a0      1       int       $argc
int (1)
0x1abcf4b1f88      1       string    &$errdir
string (43) "C:\modyfing\jbbot\app\common/../../runtime/"
Run  r

Show var
info vars 打印当前变量 auto exit
ev $var 打印变量值
ev $code 执行代码命令



单步执行 phpdbg的单步执行只有一个命令 step
。和gdb的step命令差不多。都是一行一行的执行代码。注意，phpdbg是没有next命令的。
....
prompt> s[Breakpoint #0 resolved at func#2 (opline 0x152ba40)][L19           0x152ba70 ZEND_ADD_STRING          C2      @0    ./test_phpdbg.php]>00019:     echo "function func $param\n";;
 00020: }
 00021:....


Single Step execution

phpdbg single step execution with only one command step. Similar to GDB's step command. is a line of execution code. Note that the phpdbg does not have a next command.
继续执行进入内部 和gdb一样，phpdbg的继续执行命令也是continue，简写形式为c
Until  直到下一个断点


执行php代码   使用ev命令执行任意的php
这个是phpdbg的一个特色。可以在调试的过程中使用ev命令执行任意的php代码。如：
......
prompt> ev $var = "val";
val
prompt> ev var_dump($var);string(3) "val"......
可以通过这种方式，在调试过程中动态的修改变量值，查看执行效果。。

其中有一个 help 命令可以让我们看到许多简写的命令，
我们主要使用这些简写的命令别名就可以。

prompt> help aliases
Below are the aliased, short versions of all supported commands
 e     exec                  set execution context
 s     step                  step through execution
 c     continue              continue execution
 r     run                   attempt execution
 u     until                 continue past the current l

