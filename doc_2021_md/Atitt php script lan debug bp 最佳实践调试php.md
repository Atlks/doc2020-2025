Atitt php script lan debug bp 最佳实践调试php

Echo vs log法
Echo更加简单。。
输出与debug信息昏药问题。。。
Cmd shell会遇到，html也会遇到ajax。。。

使用关闭调试法不方便。。。使用   分隔符号比较好，提取最后的数据。。这样也方便调试输出。
debug_print_backtrace

如果我们想知道某个方法被谁调用了? debug_print_backtrace可以解决
debug_print_backtrace() 可以打印出一个页面的调用过程 , 从哪儿来到哪儿去一目了然.
不过这是一个PHP5的专有函数,好在pear中已经有了实现,
http://pear.php.net/package/PHP_Compat


echo和print的区别


PHP中echo和print的功能基本相同（输出），但是两者之间还是有细微差别的。echo输出后没有返回值，但print有返回值，当其执行失败时返回flase。因此可以作为一个普通函数来使用，例如执行下面的代码后变量$r的值将为1。

$r = print "Hello World";

这意味着print可用在一些复杂的表达式中，而echo则不行。但是，因为echo语句不要求返回任何数值，所已在代码中echo语句的运行效率要略微快于print语句。

echo()
可以一次输出多个值，多个值之间用逗号分隔。echo是语言结构(language construct)，而并不是真正的函数，因此不能作为表达式的一部分使用。
print()
函数print()打印一个值（它的参数），如果字符串成功显示则返回true，否则返回false。
print_r()
可以把字符串和数字简单地打印出来，而数组则以括起来的键和值得列表形式显示，并以Array开头。但print_r()输出布尔值和NULL的结果没有意义，因为都是打印"\n"。因此用var_dump()函数更适合调试。
打印关于变量的易于理解的信息,如果给出的是 string、integer 或 float，将打印变量值本身。如果给出的是 array，将会按照一定格式显示键和元素。object 与数组类似。 记住，print_r() 将把数组的指针移到最后边。使用 reset() 可让指针回到开始处。
var_dump()
此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。
判断一个变量的类型与长度,并输出变量的数值,如果变量有值输的是变量的值并回返数据类型。此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。
var_dump和print_r的区别：
var_dump返回表达式的类型与值而print_r仅返回结果，相比调试代码使用var_dump更便于阅读。


3.print_r
打印关于变量的易于理解的信息,如果给出的是 string、integer 或 float，将打印变量值本身。如果给出的是 array，将会按照一定格式显示键和元素。object 与数组类似。 记住，print_r() 将把数组的指针移到最后边。使用 reset() 可让指针回到开始处。
4.var_dump
此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。
5.var_dump 和 print_r 的区别
var_dump 返回表达式的类型与值而 print_r 仅返回结果，相比调试代码使用 var_dump 更便于阅读
六 die
die语句也可以输出内容，不过die在输出内容后就会终止程序的运行。同样只能输出单一数据不能打印数据类型结构，也不能输出复合数据类型的数据
由于die在输出内容后就终止了程序的运行因为也不会有返回值

