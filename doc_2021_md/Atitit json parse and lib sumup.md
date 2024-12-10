Atitit json parse and lib sumup  

使用方便度  fastjson的更加简单
，，gson的比较麻烦些，代码量更多

遇到循环引用序列号，fastjson可能有问题。。。Gson梅雨哦测试，可能会好些。

3.Google的Gson
Gson是目前功能最全的Json解析神器，Gson当初是为因应Google公司内部需求而由Google自行研发而来，
但自从在2008年五月公开发布第一版后已被许多公司或用户应用。
Gson的应用主要为toJson与fromJson两个转换函数，无依赖，不需要例外额外的jar，能够直接跑在JDK上。
而在使用这种对象转换之前需先创建好对象的类型以及其成员才能成功的将JSON字符串成功转换成相对应的对象。
类里面只要有get和set方法，Gson完全可以将复杂类型的json到bean或bean到json的转换，是JSON解析的神器。
Gson在功能上面无可挑剔，但是性能上面比FastJson有所差距。
4.阿里巴巴的FastJson
Fastjson是一个Java语言编写的高性能的JSON处理器,由阿里巴巴公司开发。
无依赖，不需要例外额外的jar，能够直接跑在JDK上。
FastJson在复杂类型的Bean转换Json上会出现一些问题，可能会出现引用的类型，导致Json转换出错，需要制定引用。
FastJson采用独创的算法，将parse的速度提升到极致，超过所有json库。

