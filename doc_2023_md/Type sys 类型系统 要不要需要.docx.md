Type sys 类型系统 要不要需要


Type的出现是为了方便管理数据变量，为了性能。。

对开发效率负面影响。。不需要type


编译时间较长
Swift是一种静态类型语言，需要进行类型检查和编译优化，因此编译时间相对较长。对于大型项目来说，编译时间可能会很长，这会影响开发人员的效率和生产力。


性能优化 类型方便提升性能
开发体验
代码补全是类型系统给我们开发的最大恩惠。按完dot后自动弹出智能补全框的愉悦不亚于在峡谷抢到人头。补全信息一般需要判断字段访问的对象类型，通过类型收集补全的候补。因此没有静态类型（往往伴随来的是许多元编程，如反射）就很难做到准确的补全
另一个开发体验的优化是类型即文档。类型在某种程度上来说是对程序的标注。比如类型签名包含了代码输入与输出的信息，也表达了函数的需求，往往我们通过签名就可以猜出一个函数的用途和用法。比如在RPC框架（gRPC/thrift）调用的IDL中就包含了类型信息。我们看下service的method名字和类型，就能大概猜测出代码。

独立于程序存在的文档往往会因为代码更新而过期或不准确。而类型标注由于和代码绑定，它的正确性是被编译器保障的。

错误检查/程序验证
这点大家或多或少有体会/感觉，静态类型语言中可以在代码上线前解决掉许多低级错误，比如引用一个不存在的变量，或是访问一个不存在的属性。



缺点
啰嗦 ，可读性低

