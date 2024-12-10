Node js must top 10 lib




Atfp.js  fun sytle fun
Lodash  数组select search is good
2. 深层查找属性值
// Fetch the name of the first pet from each ownervar ownerArr = [{
    "owner": "Colin",
    "pets": [{"name":"dog1"}, {"name": "dog2"}]}, {
    "owner": "John",
    "pets": [{"name":"dog3"}, {"name": "dog4"}]}];
// Array's map method.
ownerArr.map(function(owner){
   return owner.pets[0].name;});
// Lodash
_.map(ownerArr, 'pets[0].name');

_.map 方法是对原生 map 方法的改进，其中使用 pets[0].name 字符串对嵌套数据取值的方式简化了很多冗余的代码，非常类似使用 jQuery 选择 DOM 节点 ul > li > a，对于前端开发者来说有种久违的亲切感。


7. 筛选属性 _.pick 是 _.omit 
// Naive method: Remove an array of keys from objectObject.prototype.remove = function(arr) {
    var that = this;
    arr.forEach(function(key){
        delete(that[key]);
    });};
var objA = {"name": "colin", "car": "suzuki", "age": 17};

objA.remove(['car', 'age']);
objA; // {"name": "colin"}
// Lodash
objA = _.omit(objA, ['car', 'age']);// => {"name": "colin"}
objA = _.omit(objA, 'car');// => {"name": "colin", "age": 17};
objA = _.omit(objA, _.isNumber);// => {"name": "colin"};

大多数情况下，Lodash 所提供的辅助函数都会比原生的函数更贴近开发需求。在上面的代码中，开发者可以使用数组、字符串以及函数的方式筛选对象的属性，并且最终会返回一个新的对象，中间执行筛选时不会对旧对象产生影响。
// Naive method: Returning a new object with selected propertiesObject.prototype.pick = function(arr) {
    var _this = this;
    var obj = {};
    arr.forEach(function(key){
        obj[key] = _this[key];
    });

    return obj;};
var objA = {"name": "colin", "car": "suzuki", "age": 17};
var objB = objA.pick(['car', 'age']);// {"car": "suzuki", "age": 17}
// Lodashvar objB = _.pick(objA, ['car', 'age']);// {"car": "suzuki", "age": 17}

_.pick 是 _.omit 的相反操作，用于从其他对象中挑选属性生成新的对象。


 
'chalk' console colar putput


require("esm-hook");
const chalk = require('chalk').default
console.log(chalk.blue('你好'))
Commodder node.js命令行界面的完整解决方案。
Moment.js 是一个用于解析、校验、操作、显示日期和时间的 JavaScript 工具库。



十 jarkas 大鱼 刘洋 汤姆, [04/09/2023 9:47 am]
还有库gm是一个基于GraphicsMagick的图像处理
 (https://so.csdn.net/so/search?q=%E5%9B%BE%E5%83%8F%E5%A4%84%E7%90%86&spm=1001.2101.3001.7020)库，可以让您轻松地进行各种图像处理操作。gm支持多种图像格式，包括JPEG、PNG、GIF等等，可以对图像进

十 jarkas 大鱼 刘洋 汤姆, [04/09/2023 9:48 am]
安全类 类库6. Rate Limiter
￼
node-rate-limiter-flexible，提供了灵活的速率限制功能，可用于保护应用程序免受恶意用户或恶意攻击者的攻击。它支持多种速率限制算法，包括令牌桶算法和漏斗算法，可以根据需要配置不同的限制规则

