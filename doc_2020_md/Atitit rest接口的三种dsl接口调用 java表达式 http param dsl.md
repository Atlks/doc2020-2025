Atitit rest接口的三种dsl接口调用 java表达式 http param dsl，json dsl


这样的写法没有问题的。。相当于传递dsl了。。一种是直接使用java表达式传递，不过要做些ast解析，稍微麻烦点，一种是http param dsl传递了，就是只适合一层方法调用，还有种就是json做dsl了，省去了词法解析，可以做方法链调用


