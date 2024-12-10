Nodejs 模块总结



1、创建自定义模块
使用exports方式  vs 使用module.exports方式


# 导出函数


基本用法
先看一个例子。假定有一个很简单的CommonJS模块文件foo.js。
// foo.js
module.exports = function(x) {
  console.log(x);
};
然后，还有一个main.js文件，用来加载foo模块。
// main.js
var foo = require("./foo");
foo("Hi");


导出oo

使用module.exports方式
js
复制代码
var app = {    name: '天气',    version: '1.0.0',    build: function(){        console.log('构建app')    }}module.exports = app
模块导入使用
js
复制代码
const module1 =  require('./custom_module.js')const module2 =  require('./custom_module2.js')//使用console.log(module2.name)module1.get()

 

导出mod   类似静态oo  cls


exports.reqest = function(){ console.log('request请求') } exports.get = function(){ console.log('get请求') } exports.post = function(){

 
