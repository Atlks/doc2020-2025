Php out 杂乱字符  直接使用ob清理即可


首页 微语 登录 
php清除不明输出(echo前面的回车换行符\t\n等)
2012-7-13 sysdee
有时候我们require_once()几个文件，这些文件因为前边有空格或是其它原因有输出，就会后边就会出现一系列的问题，包括 session。通过php生成图片等。

这时候找不出输出在哪。可以在这个文件头加上

最开始加上

ob_start();

require_once();

require_once();

require_once();

ob_end_clean();

这样子可以把require_once包含的文件中的不明输出去掉

