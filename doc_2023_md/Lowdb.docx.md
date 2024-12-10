Lowdb

Lodash API
lowdb3.0还支持使用lodash的api，我们需要继承一下Low这个类

各种适配器Adapter
lowdb的强大之处就是提供了各种适配器,在前文中我使用了JSONFile这个适配器，这其实是一个异步的JSON文件适配器,常用的有
JSONFile 异步的JSON文件
JSONFileSync 同步的JSON文件
Memory 异步的使用内存
MemorySync 同步的使用内存
LocalStorage 本地存储，使用这个要注意空间大小
TextFile 异步的纯文本，主要用于自定义适配器
TextFileSync异步的纯文本，主要用于自定义适配器 同时，lowdb还支持自定义适配器，你可以适配各种文件格式，数据类型

限制
官方文档中推荐lowdb的文件大小不超过100MB,因为在js中，格式化json主要用JSON.parse()和JSON.stringify,当超过100MB之后会有无法避免的性能问题。还有如果你使用localStorage， 限制应该是5MB。这也是我一开就说应用于小型服务的原因。

作者：前端冒菜师
链接：https://juejin.cn/post/7104222761031041055
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

