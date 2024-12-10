Js embd db NeDB    MongoDB 版的 SQLite



嵌入式数据库 NeDB
发布于 2018-04-03 16:15:19
2.2K
0
举报
在你开发一个程序时，有时可能需要一部分数据库的功能，但又不想单独安装一个，因为安装数据库还是比较麻烦的，也用不到数据库那么丰富的功能，单独安装数据库会感觉比较重
假设下面两个场景：
（1）你正在写一个 Node service，你希望他是可以轻松被打包的，安装独立的数据库不能满足需求
（2）使用 Node Webkit 开发了一个桌面应用，但是不想要求用户安装一个外部数据库
NeDB 是一个轻量级数据库，完全使用javascript编写，并且使用了广为使用的 MongoDB API 使用方式
NeDB 被打包成一个 Node module，只需要一个简单的 require 便可以使用
NeDB 可以只用作内存数据库，也可以进行数据持久化，你可以把 NeDB 理解为 MongoDB 版的 SQLite
NeDB的特点
实现了 MongoDB 的很多特性
（1）CRUD 和 upserts
（2）持久化数据的能力
（3）表达式查询语言，可以使用符号‘.’来查询嵌套文档，支持 正则表达式、比较操作符（$lt, $lte, $gt, $gte, $in, $nin, $exists）、逻辑操作符（$and, $or, $not）
（4）Documents 修改方法 $set, $inc, $push, $pop, $addToSet, $each
（5）提供浏览器版本
NeDB的性能
NeDB 不是用来替代像 MongoDB 这样的真实数据库的，所以他的目标不是尽可能的快，而是够用就行
NeDB 可以达到 写 5000次/秒、读 25000次/秒
如果你的需求超出了这个，那么NeDB便不适合了

