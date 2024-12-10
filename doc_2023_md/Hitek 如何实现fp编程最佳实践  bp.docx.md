Hitek 如何实现fp编程最佳实践  bp


Java static import 来实现


Node     把fun绑定到win,global等全局对象上。。然后直接requie（）
就可以了。。。

可以导出  {  fun,fun2} =requ()
然后  global[‘fun’]=fun来绑定实现全局函数fp

Php   已经支持。。

Autoload函数比较需要，，php需要定义inc路径组，然后扫描制定lib
Node直接放入node——module目录，就可以直接应用了。。Mode
就像内置模块一样了。。
