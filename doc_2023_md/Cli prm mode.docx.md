Cli prm mode


参数可以是独立的，也可以具有键和值。
例如：
BASH
node app.js joe

或
BASH
node app.js name=joe

这会改变在 Node.js 代码中获取参数值的方式。


const args = process.argv.slice(2)
args[0]

如果是这种情况：
BASH
node app.js name=joe

则 args[0] 是 name=joe，需要对其进行解析。 最好的方法是使用 minimist 库，该库有助于处理参数：
JS
const args = require('minimist')(process.argv.slice(2))
args['name'] //joe
但是需要在每个参数名称之前使用双破折号：
BASH
node app.js --name=joe


