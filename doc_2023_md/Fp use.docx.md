Fp use



十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:14 am]
基本数据类型对大多数业务相关或网络应用程序没有太大的用处，这些应用一般是采用客户端/服务器模式，后端有数据库。然而，使用基本数据类型对那种以数值计算为主的应用提升性能有很大好处

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:15 am]
你阅读这篇文章的时候，可能已经知道了Java是双类型的系统，也就是基本数据类型和对象类型，简称基本类型和对象。Java中有8个预定义的基本类型

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:18 am]
。如果性能是选择一个编程语言的主要因素的话，那么C++是数值运算密集型应用的首选

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:25 am]
基本类型武大类型  数字 子串 函数 bool

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:25 am]
基本元函数crud 加减乘除   与或非

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:25 am]
isxxx  cast

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:26 am]
isexist

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:26 am]
afmi

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:26 am]
admi  怎水果茶

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:27 am]
top20基础函数

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:28 am]
mov函数

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:28 am]
流程控制类 if while until

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:33 am]
基础物资  水粮食 燃料火 药品  房子

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:33 am]
意味着命令超过一百万人撤离到没有庇护所、没有粮食、没有水、没有药物和没有燃料的南部地区，然后又继续轰炸南

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:37 am]
副作用

副作用是修改系统状态的语言结构。因为 FP 语言不包含任何赋值语句，变量值一旦被指派就永远不会改变。而且，调用函数只会计算出结果 ── 不会出现其他效果。因此，FP 语言没有副作。。提升可靠性

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:37 am]
了，先回忆一下啥是函数式编程（FP）吧，比如FP要求使用表达式，不允许出现语句，这样更接近自然语言

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:38 am]
判断语句，枚举语句，这些都是语句，也就是说我们再熟悉不过的if/else语句，for/while循环，switch以及try/catch都不给用了！

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:38 am]
流程控制类函数 if while until trycatch

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:39 am]
if/else语句  条件运算符（… ? … : …）
函数式替换if/else语句也很简单，我们本来就有条件运算符（… ? … : …）可用：

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:40 am]

Case语句  列表调用即可 
函数组成一个列表。
try&catch语句 嗓音。裹进promise
至于try/catch/finally可以将同步流包裹进promise，再给他监听一个catch方法

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:40 am]
switch语句
switch语句的话可以用js散列表来模拟，也就是对象：

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:43 am]
循环遍历
数组的forEach方法
我们最常见的循环就是遍历一个数组，那直接可以利用数组的forEach方法来遍历：

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:43 am]
指定循环次数  构造一个定长数组
for循环语句中经常出现需要指定循环的次数而没有数组，我们可以通过构造一个定长数组来遍历：
可中断的遍历方法 find  some  every
十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:44 am]
。可喜的是，数组有一些“可中断的遍历方法”，比如find方法本意是寻找一个数组元素，找到后就可以中断遍历；比如some方法本意是是否有“一些”元素符合回调条件，遍历时一旦匹配到一个就会停止向下匹配；比如every方法本意是是否“所有”元素都符合回调条件，遍历时只要发现1个元素不符合就会停止向下匹配。所以函数式编程中有3个数组方法可以实现循环的break。

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:44 am]
// 函数式break
// find
list.find(item=>{
  if(condition)return true;
})
// some
list.some(item=>{
  if(condition)return true;
})
// every
list.some(item=>{
  if(condition)return false;
})

十 jarkas 大鱼 刘洋 汤姆, [29/10/2023 2:45 am]
无限循环递归调用自己
取代无限循环语句只要递归调用自己就好啦~

// 无限循环语句
while(true){}

// 无限循环表达式
(function loop(){
  loop();
})()