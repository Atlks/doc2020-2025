Node mod expt


ECMAScript 6 (ES6) 引入了 ES Modules 规范，提供了在 JavaScript 中实现模块的标准。
截至 2022 年，所有主要的 Web 浏览器都支持 ES 模块。
ECMAScript 模块系统（使用import和export）已经成为标准，并且 Node.js 增加了对它的支持。
然而，模块化 JavaScript 的流行早于 ES6。
Node.js 是一种 JavaScript 运行时环境，使用 CommonJs（使用require和module.exports）作为模块规范。
现有的很多应用都是用 CommonJS 构建的，所以Node.js在添加对 原生ES模块 的支持时，颇有争议地引入了MJS文件扩展名来区分两者，防止应用崩溃。
Node.js 会将.cjs文件视为 CommonJS 模块，将.mjs文件视为 ECMAScript 模块。
它会将.js文件视为项目的 默认模块系统（除非package.json说的是 CommonJS "type": "module",）。
简而言之，它是用于 Node.js 区分 CommonJS （.js）和 ES6模块文件（.mjs）。

import声明#
语句import可以引用 ES 模块或 CommonJS 模块。 import仅允许在 ES 模块中使用语句，但import() CommonJS 支持动态表达式来加载 ES 模块。
导入CommonJS 模块时，该 module.exports对象作为默认导出提供。命名导出可能是可用的，由静态分析提供，以方便更好的生态系统兼容性。



那如果两种模块我都想用怎么办？，是不是直接 .js 就行了？
结果并不是，.js 会去 package.json 文件中寻找你的 type 字段来当规范，如果没有 type 字段，默认为 CommonJs 规范
如果两种模块都想用的话，最简单的就是使用 ES 模块，用 import() 导入 CommonJs 的代码

 
Node.js 里可分为 CommonJS 模块和 ECMAScript 模块（ESM）两种不同的模块系统。
CommonJS 模块是 Node.js 最初支持的模块系统，它使用 require() 函数来导入模块，使用 module.exports 或 exports 对象来导出模块。这种模块系统通常只能在 Node.js 环境下使用，并且不允许在浏览器环境中使用。
ECMAScript 模块是 JavaScript 的标准模块系统，它使用 import 和 export 关键字来导入和导出模块。它可以在 Node.js 环境下和现代浏览器环境中使用，具有更好的跨平台兼容性和可移植性。Node.js 从版本12开始支持 ECMAScript 模块作为实验性功能，并在版本14中正式支持。

 


https: //api.etherscan.io/api?module=block&action=getblocknobytime&timestamp=999&closest=before&apikey=VASRGU6XT768WSKI2VME6Z8ZK3GK5E3UDT

    function timeA() { console.log('Function timeA in a.js.') }

module.exports = {
    timeA,
    ff() { console.log('Function fff in b.js.') },
    ff2() { console.log('Function fff in b.js.') },
    B_A() { console.log('Function B_A in b.js.') },
    async http_get(url) {







const { ff } = require('./http.js');

//var { ff2 } = require('./http.js');
// ff2 = require('./http.js'); err

var { ff2 } = require('./http.js');

ff();
ff2();

var { timeA } = require('./http.js');
timeA();

