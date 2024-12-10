Atitit mysql的reset接口

参考MongoDB的比较简单
同时加上limit限制和skip限制
http://127.0.0.1:28017/databaseName/collectionName/?skip=5&limit=10
按条件{a:1}进行结果筛选（在关键字filter后面接上你的字段名）
http://127.0.0.1:28017/databaseName/collectionName/?filter_a=1


执行任意命令
如果你要执行特定的命令，可以通过在admin.$cmd上面执行find命令，同样的你也可以在REST API里实现，如下，执行{listDatabase:1}命令：
http://localhost:28017/admin/$cmd/?filter_listDatabases=1&limit=1


Es的查询

任意一个查询后再加上 ?pretty 就可以生成 更加美观 的JSON反馈，以增强可读性。
请求表结构元数据GET /db/table/_source


GET /db/table/_source
