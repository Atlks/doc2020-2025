Atitit 源码语句解析结构


栈帧（Stack Frame）是用于支持虚拟机进行方法调用和方法执行的数据结构，它是虚拟机运行时数据区中的虚拟机栈（Virtual Machine Stack）的栈元素。栈帧存储了方法的局部变量表、操作数栈、动态连接和方法返回地址等信息。每一个方法从调用开始至执行完成的过程，都对应着一个栈帧在虚拟机栈里面从入栈到出栈的过程。

而什么是栈帧(Stack Frame)呢?
每一次函数的调用,都会在调用栈(call stack)上维护一个独立的
栈帧(stack frame).每个独立的栈帧一般包括:
函数的返回地址和参数
临时变量: 包括函数的非静态局部变量以及编译器自动生成的其他临时变量
函数调用的上下文
栈是从高地址向低地址延伸,一个函数的栈帧用ebp 和 esp 这两个寄存器来划定范围.ebp 指向当前的栈帧的底部,esp 始终指向栈帧的顶部;</br>
ebp 寄存器又被称为帧指针(Frame Pointer);</br>
esp 寄存器又被称为栈指针(Stack Pointer);


 

局部变量表（Local Variable Table）
局部变量表（Local Variable Table） 是一组变量值存储空间，用于存放方法参数和方法内部定义的局部变量。在 Java 程序编译为 Class 文件时，就在方法的 Code 属性的 max_locals 数据项中确定了该方法所需要分配的局部变量表的最大容量。

ref
Atitit xml xpath以及mybatis xml mapper脱机解析

