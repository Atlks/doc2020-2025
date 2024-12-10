Hiapi shell fun


exec() - 执行一个外部程序  返回 命令执行结果的最后一行内容。
escapeshellcmd() - shell 元字符转义
escapeshellarg — 把字符串转义为可以在 shell 命令里使用的参数

shell_exec — 通过 shell 执行命令并将完整的输出以字符串的方式返回
passthru — 执行外部程序并且显示原始输出
system — 执行外部程序，并且显示输出




同 exec() 函数类似， passthru() 函数 也是用来执行外部命令（command）的。 当所执行的 Unix 命令输出二进制数据， 并且需要直接传送到浏览器的时候， 需要用此函数来替代 exec() 或 system() 函数。 常用来执行诸如 pbmplus 之类的可以直接输出图像流的命令。 通过设置 Content-type 为 image/gif， 然后调用 pbmplus 程序输出 gif 文件， 就可以从 PHP 脚本中直接输出图像到浏览器。





exec() 执行 command 参数所指定的命令。 
参数 ¶
command
要执行的命令。 
output
如果提供了 output 参数， 那么会用命令执行的输出填充此数组， 每行输出填充数组中的一个元素。 数组中的数据不包含行尾的空白字符，例如 \n 字符。 请注意，如果数组中已经包含了部分元素，exec() 函数会在数组末尾追加内容。如果你不想在数组末尾进行追加， 请在传入 exec() 函数之前 对数组使用 unset() 函数进行重置。 
result_code
如果同时提供 output 和 result_code 参数，命令执行后的返回状态会被写入到此变量。 
返回值 ¶
命令执行结果的最后一行内容。 如果你需要获取未经处理的全部输出数据， 请使用 passthru() 函数。 
失败时返回 false。 
如果想要获取命令的输出内容， 请确保使用 output 参数

