Im  Tg接受消息  tlgrm msg rcv


telegram更新
telegram中更新指的是机器人是否有收到新的消息，具体有哪些消息可以查看telegram对象部分中的Update，获取更新的方式有两种1. 轮询，2.webhook
轮询
这是一种主动询问的方式，这种方式比较简单但是效率欠佳，具体操作是，开发者每个一段时间请求一次getUpdates方法，从获取结果中判断update有无更新，有关update对象的描述可看telegram对象章节
webhook
webhook可以理解为客户端给服务端的api,只要服务端一有更新就会主动将内容发送到客户端设置的一个api中，然后客户端收到消息后可做相应处理。
给我们的机器人设置webhook
通过setWebhook方法设置（前面有介绍），需要注意的是，telegram只支持https协议，所以我们的api服务器必须要有TLS证书，必须注意一但我们设置了webhook那么通过getUpdates方法将不起作用！

