Php hilev exec code fun



程序执行函数 ¶
注释 ¶
警告 
以加锁方式打开的文件（特别是在打开会话时）， 必须在执行后台程序之前关闭。 
参见 ¶
这些函数和 执行运算符 是紧密关联的。 
目录 ¶
escapeshellarg — 把字符串转义为可以在 shell 命令里使用的参数
escapeshellcmd — shell 元字符转义
exec — 执行一个外部程序
passthru — 执行外部程序并且显示原始输出
proc_close — 关闭由 proc_open 打开的进程并且返回进程退出码
proc_get_status — 获取由 proc_open 函数打开的进程的信息
proc_nice — 修改当前进程的优先级
proc_open — 执行一个命令，并且打开用来输入/输出的文件指针。
proc_terminate — 杀死由 proc_open 打开的进程
shell_exec — 通过 shell 执行命令并将完整的输出以字符串的方式返回
system — 执行外部程序，并且显示输出
eval
