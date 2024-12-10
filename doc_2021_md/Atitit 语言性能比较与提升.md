Atitit 编程 语言性能比较与提升

Sql性能，特别是sp编译后性能很高， 可能有jit和编译为机器码
但sql在mysql上对调试与异常处理繁琐。。可以分解为多个子程序。。每个单独处理异常等。。
默认终止模式，，可以catch为revoer恢复模式。。。

Sql不支持fib数列，说不能递归。。只要用循环测试，加减乘除与字符串连接


Oracle 数据库将SQL 语句运行时转换为C\C++ 代码，然后将其编译为机器码。 Postgres 11 中提供了基于LLVM 的即时编译(JIT) 的SQL 语句执行 ..
Go和java

Nodejs  性能也不错。
数列测试性能是php对十倍以上，但异步很操蛋。。  和单线程 可以做cluser
Php7
Python性能最差类。。

