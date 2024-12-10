Atitt node mod 机制 mache

在Node中每一个js文件都是一个单独的模块
这个模块中包括CommonJS规范的核心变量：exports、module.exports、require
·  exports和module.exports可以负责对模块中的内容进行导出
·  两者都是一个对象
·  // 使用另外一个模块导出的对象, 那么就要进行导入 require const { name, age, sum } = require("./xxx.js") console.log(name); console.log(age); console.log(sum(20, 30));

作者：一条小鱼子
链接：https://juejin.cn/post/7097581777484513310
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。





exports

第二种导出方式：

// a.js
exports.name = name
exports.age = age
exports.sum = sum

// b.js
const xxx = require("./a.js")




export关键字

export关键字将一个模块中的变量、函数、类等导出

方式一：export声明语句

export const name = "xxx"
export const age = 18
export function bar() {}
export class Person {}




16

值得注意的是，在 ES6 中，您现在可以像这样导出函数：
export function foo(){}
export function bar(){}

export只需在要导出的函数之前写入即可







There are four forms of import declarations:
Named import: import { export1, export2 } from "module-name";
Default import: import defaultExport from "module-name";
Namespace import: import * as name from "module-name";
Side effect import: import "module-name";
Note: JavaScript does not have wildcard imports like import * from "module-name", because of the high possibility of name conflicts.



How to ijmpt all fun..not as modname ...

个棘手的解决方法可能是const myMod = require('myMod')先映射它，然后将函数放在全局对象上。或者从一开始就将它们放在全局中而不是导出它。


果一个文件中有 100 个导出，并且想要调用所有这些导出，则问题可能是另一种性质。你可以做类似的事情Object.values(mymod).forEach(f => f())。
