Dev lan choose solu



Stp dbg

2.这就涉及到代码提示了，很多IDE对PHP都不是很友好。虽然有些集成好的，但都是重型开发框架，就算要单步调试，也要配置很多选项。node不一样，代码追踪，补全，报错，单步调试都简单出了一个量级。
3.node的开发环境 n 扩展
撘起来不要太简单，下个node安装一下就完事。PHP则要安装ng或A而且安装PHP还要关心需要哪些扩展。如果纯自己搭建node1分钟，

知乎用户ijRDu4
同样觉得php安装麻烦，虽然现在docker拉一个镜像就行了


HP开发环境优于node的地方：

dev node来解决即可，方便热更新

node，其实文件改变了不会立刻生效，用插件监听到文件变化，再重新编译一下。不用插件则手动重新编译。而PHP文件一改变，刷新页面立刻生效。

这个可以使用dev node来解决即可，方便热更新


回调地狱  await解决

现在都2017年，ES2018都发布了，还有人拿回调地狱说事。这几年的发展，不都是为了填语言的坑吗。Node8已经是LTS, 你想要的新特性，基本都已经支持。还有人说是动态语言一时爽，Typescript笑而不语

当然是 PHP 爽，没有 Once await ,never back 的问题。
就是本来一个同步的函数改异步，导致所有东西都要改



