Es prblm 


// CommonJS模块其实就是对象，输入时必须查找对象属性。let {stat,exists,readfile} = require('fs');// 相当于let _fs = require('fs');let stat = _fs.stat;let exists = _fs.exists;let readfile = _fs.readfile;// 此处代码实质：整体加载fs模块（加载fs的所有方法），生成一个对象（_fs）,然后从对象上面读取方法。// 这种加载称为运行时加载，只有运行时才能的到这个对象,导致完全没办法在编译时做静态优化。复制
// ES6模块import {stat,exists,readFile} from 'fs';// 此处代码实质：从fs模块加载3个方法，其他方法不加载。这种加载称为编译时加载或者静态加载，即ES6可以在编译时就完成模块加载，效率要比CommonJS模块的加载方式高


2.严格模式

ES6的模块自动采用严格模式，不管是否使用‘use strict’关键字。


ES6自动采用严格模式，严格模式的限制有哪些呢

·  变量必须声明后再使用
·  函数的参数不能有同名属性，否则报错
·  不能使用with语句
·  不能对只读属性赋值，否则报错
·  不能使用前缀 0 表示八进制数，否则报错
·  不能删除不可删除的属性，否则报错
·  不能删除变量delete prop，会报错，只能删除属性delete global[prop]
·  eval不会在它的外层作用域引入变量
·  eval和arguments不能被重新赋值
·  arguments不会自动反映函数参数的变化
·  不能使用arguments.callee
·  不能使用arguments.caller
·  禁止this指向全局对象
·  不能使用fn.caller和fn.arguments获取函数调用的堆栈
·  增加了保留字（比如protected、static和interface）

如何使用宽松模式  不需要先声明变量


⑨ import可以后面直接跟模块名，加载一整个模块 import ‘lodash’
① 可以使用 * 来加载一个模块的所有输出的接口
