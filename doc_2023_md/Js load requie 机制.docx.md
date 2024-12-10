Js load requie 机制


require和module.exports不是黑魔法
我们通过前面的例子可以看出来，require和module.exports干的事情并不复杂，我们先假设有一个全局对象{}，初始情况下是空的，当你require某个文件时，就将这个文件拿出来执行，如果这个文件里面存在module.exports，当运行到这行代码时将module.exports的值加入这个对象，键为对应的文件名，最终这个对象就长这样：
{
  "a.js": "hello world",
  "b.js": function add(){},
  "c.js": 2,
  "d.js": { num: 2 }
}
当你再次require某个文件时，如果这个对象里面有对应的值，就直接返回给你，如果没有就重复前面的步骤，执行目标文件，然后将它的module.exports加入这个全局对象，并返回给调用者。这个全局对象其实就是我们经常听说的缓存。所以require和module.exports并没有什么黑魔法，就只是运行并获取目标文件的值，然后加入缓存，用的时候拿出来用就行。再看看这个对象，因为d.js是一个引用类型，所以你在任何地方获取了这个引用都可以更改他的值，如果不希望自


加载文件夹
前面提到找不到文件就找文件夹，但是不可能将整个文件夹都加载进来，加载文件夹的时候也是有一个加载顺序的：
先看看这个文件夹下面有没有package.json，如果有就找里面的main字段，main字段有值就加载对应的文件。所以如果大家在看一些第三方库源码时找不到入口就看看他package.json里面的main字段吧，比如jquery的main字段就是这样："main": "dist/jquery.js"。
如果没有package.json或者package.json里面没有main就找index文件。
如果这两步都找不到就报错了

