Go lan bp



由于 Go 支持 “多值返回”_ 来丢弃不需要的返回值

, 而对于 “声明而未被调用” 的变量，编译器会报错，在这种情况下，可以使用 _ 来丢弃不需要的返回值

函数当做值和类型在我们写一些通用接口的时候非常有用，通过上面例子我们看到 testInt 这个类型是一个函数类型，然后两个 filter 函数的参数和返回值与 testInt 类型是一样的，但是我们可以实现很多种的逻辑，这样使得我们的程序变得非常的灵活。

————————————————
Panic 和 Recover

Go 没有像 Java 那样的异常机制，它不能抛出异常，而是使用了 panic 和 recover 机制。一定要记住，你应当把它作为最后的手段来使用，也就是说，你的代码中应当没有，或者很少有 panic 的东西。这是个强大的工具，请明智地使用它。那么，我们应该如何使用它呢？

————————————————
main 函数和 init 函数

Go 里面有两个保留的函数：init 函数（能够应用于所有的 package ）和 main 函数（只能应用于 package main）。这两个函数在定义时不能有任何的参数和返回值。虽然一个 package 里面可以写任意多个 init 函数，但这无论是对于可读性还是以后的可维护性来说，我们都强烈建议用户在一个 package 中每个文件只写一个 init 函数。

————————————————
Go 程序会自动调用 init() 和 main()，所以你不需要在任何地方调用这两个函数。每个 package 中的 init 函数都是可选的，但 package main 就必须包含一个 main 函数。

程序的初始化和执行都起始于 main 包

————————————————
当一个包被导入时，如果该包还导入了其它的包，那么会先将其它包导入进来，然后再对这些包中的包级常量和变量进行初始化，接着执行 init 函数（如果有的话），依次类推。等所有被导入的包都加载完毕了，就会开始对 main 包中的包级常量和变量进行初始化，然后执行 main 包中的 init 函数（如果存在的话），最后执行 main 函数。下图详细地解

————————————————
Fp编程，不要前缀模块

点操作

我们有时候会看到如下的方式导入包

import (
    . "fmt"
)

这个点操作的含义就是这个包导入之后在你调用这个包的函数时，你可以省略前缀的包名，也就是前面你调用的 fmt.Println ("hello world") 可以省略的写成 Println ("hello world")

————————————————
_操作

这个操作经常是让很多人费解的一个操作符，请看下面这个 import


import (
    "database/sql"
    _ "github.com/ziutek/mymysql/godrv"
)

_操作其实是引入该包，而不直接使用包里面的函数，而是调用了该包里面的 init 函数。

————————————————
原文作者：Go &#25216;&#26415;&#35770;&#22363;&#25991;&#26723;&#65306;&#12298;Go Web &#32534;&#31243;&#65288;&#65289;&#12299;
转自链接：https://learnku.com/docs/build-web-application-with-golang/023-processes-and-functions/3161#726011
版权声明：著作权归作者所有。商业转载请联系作者获得授权，非商业转载请保留以上作者信息和原文链接。
