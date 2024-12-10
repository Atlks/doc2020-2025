Atitit lambda表达式



 Lambda 表达式。它们只是创建函数的表达式
大多数现代编程语言（Python、Ruby、Java...）中都存在 Lambda 表达式。它们只是创建函数的表达式。这对于支持一流函数的编程语言来说非常重要，这基本上意味着将函数作为参数传递给其他函数或将它们分配给变量。
在 ES6 之前的 JavaScript 中，我们有函数表达式，它给我们一个匿名函数（一个没有名字的函数）。
var anon = function (a, b) { return a + b };


句法
基本语法
一个参数。不需要简单的表达式返回：
param => expression
复制到剪贴板
多个参数需要括号。不需要简单的表达式返回：
(param1, paramN) => expression
复制到剪贴板
多行语句需要正文括号并返回：
param => {
  let a = 1;
  return a + param;}
复制到剪贴板
多个参数需要括号。多行语句需要正文括号并返回：
(param1, paramN) => {
   let a = 1;
   return a + param1 + paramN;}
复制到剪贴板
高级语法
要返回一个对象字面量表达式，需要在表达式周围加上括号：
params => ({foo: "a"}) // returning the object {foo: "a"}
复制到剪贴板
支持其余参数：
(a, b, ...r) => expression
复制到剪贴板
支持默认参数：
(a=400, b=20, c) => expression
复制到剪贴板
解构 PARAMS中支持：
([a, b] = [10, 20]) => a + b;  // result is 30({ a, b } = { a: 10, b: 20 }) => a + b; // result is 30

