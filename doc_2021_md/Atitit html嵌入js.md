Atitit html嵌入js


嵌入变量
模板字符串支持嵌入变量，只需要将变量名写在 ${} 之中，其实不止变量，任意的 JavaScript 表达式都是可以的：
let x = 1, y = 2;let message = `<ul><li>${x}</li><li>${x + y}</li></ul>`;console.log(message); // <ul><li>1</li><li>3</li></ul>
ES6 系列之模板字符串 - SegmentFault 思否
