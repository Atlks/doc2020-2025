Hitek runtime





十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:23 am]
高级技术异常的实现机制   try catch模式和register ex hdlr模式。。。解析器的实现，运行代码。检测结果，如果失败给全局设置Stack调用信息，把异常ex封装为obj，，寻找当前块注册wx hdlr,,yaosi ok find,,then goto catch block

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:23 am]
高级技术 rt 运行时的实现

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:24 am]
rt的实现。。调用语言解析器和类库模式。。#安全自己实现解析器模式 比较麻烦些

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:26 am]
高级技术 实现自己的解析器  状态机 麻烦

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:26 am]
框架frm的实现  回调机制   回调函数麻烦。。使用cfg文件 eval模式

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:27 am]
timer的实现  多任务管理 单线程  evt 循环loop

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:35 am]
自己实现中间件  os 数据库 等

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:36 am]
如何实现阻塞是队列，类似rds

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:38 am]
lopp循环。一但data了。立即echo输出即可

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:42 am]
高级技术  实现语言本身解析器，，实现rtm运行时  实现db  rds中间件。实现mvc框架

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:43 am]
runtime的实现
在编程语言中，runtime通常是由编译器和运行时库共同实现的。编译器负责将源代码编译成可执行代码，而运行时库则负责在程序运行时提供各种运行时支持和服务。运行时库通常包括了各种系统库和标准库，以及一些特定于编程语言的库和框架。

在C语言中，runtime的实现通常是由C库和操作系统共同提供的。C库提供了各种常用的函数和数据类型，而操作系统则提供了一些底层的系统调用和服务。在Java语言中，runtime的实现则是由Java虚拟机（JVM）和Java类库共同提供的。JVM负责将Java字节码编译成可执行代码，并提供各种运行时支持和服务，而Java类库则提供了各种常用的类和函数。

十 jarkas 大鱼 刘洋 汤姆, [14/08/2023 2:44 am]
高级技术 实现复杂界面输出  绘图模式。。实现事件机制，获取鼠标坐标，响应事件