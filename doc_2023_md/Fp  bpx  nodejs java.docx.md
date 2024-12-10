Fp  bpx  nodejs java



Static  import  java 

Js 命名导入函数
const {readFileSync,writeFileSync,appendFileSync} = require("fs");


mport 分为命名式导入（名称导入）和定义式导入（默认导入）


按名称导出  通常首选应该使用按命名导出。
如前所述，使用 export 语法将允许分别导入按名称导出的值。例如，使用以下简化版本的 function.js：
export function sum() {}export function difference() {}
这将允许使用花括号按名称导入 sum 和 difference：
import { sum, difference } from "./functions.js";
也可以使用别名来重命名该函数以避免在同一模块中命名冲突。在此示例中，sum 将重命名为 add，difference 将重命名为 subtract。
import { sum as add, difference as subtract } from "./functions.js";
因此，通常首选应该使用按命名导出。与按命名导出不同，默认导出不需要标识符 —— 基础类型的值或匿名函数都可以用作默认导出。下面是用作默认导出的对象的示例：

Global  expt node
