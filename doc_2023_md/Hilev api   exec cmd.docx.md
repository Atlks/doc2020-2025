Hilev api   exec cmd



exec 执行系统外部命令时不会输出结果，而是返回结果的最后一行，如果你想得到结果你可以使用第二个参数，让其输出到指定的数组，此数组一个记录代表输出的一行，即如果输出结果有20行，则这个数组就有20条记录，所以如果你需要反复输出调用不同系统外部命令的结果，你最好在输出每一条系统外部命令结果时清空这个数组，以防混乱。第三个参数用来取得命令执行的状态码，通常执行成功都是返回０。


passthru与system的区别，passthru直接将结果输出到浏览器，不需要使用 echo 或 return 来查看结果，不返回任何值，且其可以输出二进制，比如图像数据。


system和exec的区别在于system在执行系统外部命令时，直接将结果输出到浏览器，不需要使用 echo 或 return 来查看结果，如果执行命令成功则返回true，否则返回false。第二个参数与exec第三个参数含义一样。

方法四：反撇号`和shell_exec()
shell_exec() 函数实际上仅是反撇号 (`) 操作符的变体


shell_exec
(PHP 4, PHP 5, PHP 7, PHP 8)
shell_exec — Execute command via shell and return the complete output as a string

