Go prgrm bpx



选择标识符是为了清晰，而不是简洁
好的名字很简洁。 好的名字不一定是最短的名字，但好的名字不会浪费在无关的东西上。好名字具有高的信噪比。

好的名字是描述性的。 好的名字会描述变量或常量的应用，而不是它们的内容。好的名字应该描述函数的结果

————————————————
好的名字应该是可预测的。
 你能够从名字中推断出使用方式。~ 这是选择描述性名称的功能，但它也遵循传统。


不要注释不好的代码，将它重写

    Don’t comment bad code — rewrite it — Brian Kernighan

粗劣的代码的注释高亮显示是不够的。 如果你遇到其中一条注释，则应提出问题，以提醒您稍后重构。 只要技术债务数额已知，它是可以忍受的。

标准库中的惯例是注意到它的人用 TODO(username) 的样式来注释。

4.3. 尽早 return 而不是深度嵌套

由于 Go 语言的控制流不使用 exception，因此不需要为 try 和 catch 块提供顶级结构而深度缩进代码。Go 语言代码不是成功的路径越来越深地嵌套到右边，而是以一种风格编写，其中随着函数的进行，成功路径继续沿着屏幕向下移动。 我的朋友 Mat Ryer 将这种做法称为 “视线” 编码。[4]

————————————————
 guard clauses buyao 嵌套 先处理错误避免嵌套
\这是通过使用 guard clauses 来实现的；在进入函数时是具有断言前提条件的条件块。，因此 Go 语言更喜欢使用 guard clauses 并尽早返回错误。


5. 项目结构
我们来谈谈如何将包组合到项目中。
5.1. 考虑更少，更大的包
对于从其他语言过渡到 Go 语言的程序员来说，我倾向于在代码审查中提到的一件事是他们会过度使用包。
在 Go 语言中，我们只有两个访问修饰符，public 和 private，由标识符的第一个字母的大小写表示。 如果标识符是公共的，则其名称以大写字母开头

我的建议是选择更少，更大的包。 你应该做的是不创建新的程序包。 这将导致太多类型被公开，为你的包创建一个宽而浅的 API。


5.1.2. 优先内部测试再到外部测试

go tool 支持在两个地方编写 testing 包测试。假设你的包名为 http2，您可以编写 http2_test.go 文件并使用包 http2 声明。这样做会编译 http2_test.go 中的代码，就像它是 http2 包的一部分一样。这就是内部测试。

go tool 还支持一个特殊的包声明，以 test 为结尾，即 package http_test。这允许你的测试文件与代码一起存放在同一个包中，但是当编译时这些测试不是包的代码的一部分，它们存在于自己的包中。就像调用另一个包的代码一样来编写测试。这被称为外部测试。

我建议在编写单元测试时使用内部测试。这样你就可以直接测试每个函数或方法，避免外部测试干扰。

————————————————
避免复杂的包层次结构，抵制应用分类法