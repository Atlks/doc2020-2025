Atitit 常见的web后端接口与接口功能总结	


接口的本质是提供一个http的sdk，
方法调用  
方法名传递
方法名应藏在url，或者通过注解在query里面，不能通过位置参数固定
或者dsl模式传递
参数传递通过url的模式
http参数，dsl模式传递参数
如何更好的实现接口
调用方法，传递参数dsl化

接口分类
数据库类 查询数据库 操作数据
数据库与结构化存储类redis等 mongodb mq
Io文件类 文件读写 上传下载


实时通知类Websocket接口
给Websocket接口发送数据

操作cookie sessioln
存储类交互类 Email sms类

调用方法执行
执行当前项目的class / 函数（预加载模式
执行当前项目的class / 函数（classload模式

执行脚本（mybatis sql sp php python js）

执行任意位置的class/函数 （web转cmd接口）

执行shell

操作内存数据  变量读写 

接口组合
（查询数据库，然后发送websocket通知）


