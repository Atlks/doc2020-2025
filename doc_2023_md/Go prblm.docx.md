Go prblm


Zhaobdao def fun....same pkg

But in ide is all ok..just dbg op,,,rebuild..then ok...

Only run is cant ...


Godoc swag also not easy install use

Dongtai invk fun..maosi only method invk



当然 JavaScript 还有很多方式可以支持动态调用函数。但是今天主要介绍的是 Go 中的动态调用函数。
无参数动态调用
Go 中想要动态调用函数，需要通过反射的方式来实现。而且其应该是对某个类型进行反射，然后获取到其相关的属性。
type my struct{}func (m *my)m1(){}//----main---mname="m1"funcs := reflect.ValueOf(&my{})f := funcs.MethodByName(mname)f.call()



定义fun类型  
第 13 行，将变量 f 声明为 func() 类型，此时 f 就被俗称为“回调函数”，此时 f 的值为 nil。
第 15 行，将 fire() 函数作为值，赋给函数变量 f，此时 f 的值为 fire() 函数。


给变量赋值fun类型。。。动态调用变量函数。。
