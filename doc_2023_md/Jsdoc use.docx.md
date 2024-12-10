Jsdoc use



，大部分时候JSDoc都能代替TypeScript

如果是写业务，大部分时候JSDoc都能代替TypeScript，对于一般业务中的类型我们不会遇到特别离谱的体操. 在业务中遇到的类型最多也就是的type-challenges 里hard的 
Cmd use

如果使用 -r 命令行标志启用递归，JSDoc 将搜索 10 层深的文件（recurseDepth）
·  JSDoc 允许您使用无法识别的标签（tags.allowUnknownTags）；
·  标准 JSDoc 标签和 closure 标签被启用（tags.dictionaries）；
·  @link标签呈现在纯文本（templates.cleverLinks，templates.monospaceLinks


指定输入文件
source 选项组结合给 JSDoc 命令行的路径，确定哪些文件要用 JSDoc 生成文档

Cfg 
Shegnch doc  npm run jsdoc

Jsdoc use
Type chk
在js代码中第一行增加// @ts-check就成功开启了类型校验了，非常简单

变量类型声明
// @ts-check
/** @type {string} */var str = '123';
/** @type {number} */var num = 123;
/** @type {{ a: number; }} */var obj = { a: 123 };
/** @type {number[]} */var arr = [1, 2, 3];
/** @type {() => number} */var fn = () => 123;
/** @type {*} */var any = 'any';
/** @type {unknown} */var unknown;


激活检查
为了确保您不仅能够获得类型信息，而且在编辑器中（或通过tsc）获得实际的错误反馈，请激活源文件中的@ts-check标志：
// @ts-check


 @ts-ignore 标志：
如果有一个特定的行出错，但你知道这样更好，请添加 @ts-ignore 标志：
// @ts-ignoreaddVAT('1200', 0.1); // would error otherwise

三种标记 @type   @param  @return
JSDoc 提供了很多种标记，用于各种场景。 
但并不是所有的都是常用的（而且使用了 vscode 以后，很多需要手动指定的标记，编辑器都能够代替你完成），常用的无外乎以下几个：
@type 标识变量类型
@param 标识函数参数类型及描述
@return 标识函数返回值类型及描述
完整的列表可以在这里找到 Block tags 
基本上使用以上三种标记以后，已经能够解决绝大部分的问题。



Prb lm solu
 Binding 'arguments' in strict mode. (195:22)
Use script mode ,,kweson mode...

"sourceType": "script",






Npm run jsdoc   npm ERR! missing script: jsdoc

npm ERR! missing script: jsdoc
But only jsdoc just ok...


Add package.json  .add jsdoc cmd
"scripts": {
 "test": "echo \"Error: no test specified\" && exit 1",
 "start": "electron .",
 "jsdoc": "jsdoc ."
},

