Nam conflct solu 命名冲突解决


命名冲突的问题等
当然对于这个问题，早期也有解决方式：立即函数调用表达式
因为早期，只有函数有自己的作用域
// index.jsvar moduleA = (function() {  var name = "xxx"  var age = 18  var isFlag = true  return {    name: name,    isFlag: isFlag  }})()





/ xxx.js(function() {  if (moduleA.isFlag) {    console.log("我的名字是" + moduleA.name)  }})()



CommonJS规范和Node关系
CommonJS是一个规范，最初提出来是在浏览器以外的地方使用，并且当时被命名为ServerJS，后来为了 体现它的广泛性，修改为CommonJS，平时我们也会简称为CJS。
Node是CommonJS在服务器端一个具有代表性的实现
Browserify是CommonJS在浏览器中的一种实现
webpack打包工具具备对CommonJS的支持和转换

作者：一条小鱼子
链接：https://juejin.cn/post/7097581777484513310
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

