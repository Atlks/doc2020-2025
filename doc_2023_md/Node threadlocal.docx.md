Node threadlocal


在 Node 中通过 Async Hooks 实现请求作用域

Async Hooks 一个实际的使用场景是存储请求上下文，在异步调用之间共享数据。


在 Node.js 中我们的业务通常都工作在主线程(使用 work_threads 除外)，是没有 ThreadLocal 类的。并且以事件驱动的方式来处理所有的 HTTP 请求，每个请求过来之后又都是异步的，异步之间还很难去追踪上下文信息，我们想做的是在这个异步事件开始，例如从接收 HTTP 请求到响应，能够有一种机可以让我们随时随地去获取在这期间的一些共享数据，也就是我们本节所提的异步本地存储技术。



const async_hooks = require('async_hooks');

// 返回当前异步作用域的asyncId
const eid = async_hooks.executionAsyncId();
//this eid just threadlocal id hah ..

Then use global[fafdadf+eid]可以存储资源了。。



function getcurReqID() {
   const async_hooks = require('async_hooks');

 //  let async_hooks=global['async_hooks']
   // 返回当前异步作用域的asyncId
   const eid = async_hooks.executionAsyncId();

// 返回触发此异步操作的异步作用域的asyncId
   const tid = async_hooks.triggerAsyncId();
   return eid
}
但是如果有await lowdb的时候，再次获取asyncid就不兑了。。注释掉lowdb代码就ok了。。
