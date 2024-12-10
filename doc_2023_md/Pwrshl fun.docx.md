Pwrshl fun


Ide  vscode
Run
 powershell -ExecutionPolicy ByPass -File "c:\modyfing\apiprj\jbbot\zmng\libx\hl.ps1"


Comm funb
Echo

Write-Host



Io file

Get-Content，获取指定位置的项的内容。
语法：Get-Content [-Path] <文件路径>
[-Path]由方括号引起，表示可以写，也可以不写；不写则默认后面是文件路径，写了就指名道姓的说后面是文件路径。 

直接运行这样一个命令，PowerShell将会把文件的内容输出到控制台上，如果你是想看看文件的内容，那这样做就Perfect！
但有时候，你想玩点高难度的运作——想把文件翻开来对里面的内容进行修改，那后面你可以用管道来把它传出去，或者直接把它赋值给一个变量。举例如下：
$file = Get-Content "d:\1.txt"
Get-Content "d:\1.txt" | %{Write-Host $_.Replace("日","太阳")} #这样就可以实现把d:\1.txt的内容，逐一输出，并把“日”字，替换为太阳。

获取文件的前N行，这也是一个有趣的事。可以用一句PowerShell来搞定。举例如下：
Get-Content d:\1.txt -totalcount 100 | set-Content top100.txt
说明：这里的Set-Content top100.txt是把前面一个语句的结果，写一个新的文件——top100.txt

如果这个时候，你想获取文件的第100行，你会不会想到去做一个很复杂的循环？如果是，那说明你有很好的编程素养。但是PowerShell告诉你不用如此麻烦。举例如下：
(Get-Content d:\1.txt -TotalCount 100)[-1]
说明：啥！你看到了啥？！如果你简单的看()[-1]，那是不是像数组呢？-1表示最后一个数组元素，那就表示前100行的最后一行，那是不是第100行呢？！ 

最后要说一下，这个命令返回的是一个对象数组，可以用ForEach-Object(别名是%)去遍历它。非常方便，前面你应该已经看到“太阳”的例子了！ 
"Hello World!" | Out-File d:\1.txt
Io net http
invoke-webrequest
Str arr
powershell字符串操作 - 一个有故事的devops - 博客园

PowerShell中调用外部程序


