Atitit  架构-简化开发-事件驱动的架构.docx 事件驱动的架构


大型软件里面，使用mq或观察者模式解耦，变成事件驱动，消息总线模式是非常好的。。


　　知乎这个产品有一个特点，最早在添加一个答案后，后续的操作其实只有更新通知、更新动态。但是随着整个功能的增加，又多出了一些更新索引、更新计数、内容审查等操作，后续操作五花八门。如果按照传统方式，维护逻辑会越来越庞大，维护性也会非常差。这种场景很适合事件驱动方式，所以开发团队对整个架构做了调整，做了事件驱动的架构。


其核心思想是，事件流可以作为已发生事件的记录加以处理，并且，任何系统或应用程序都可以实时利用它来对数据流做出反应、响应或进行处理。
这有着非常重要的意义。在公司内部，通常是一团乱麻似的相互连接的系统，每个应用程序都临时与另外一个连接。这是非常昂贵耗时的方法。事件流提供了一种替代方法：可以有一个中央平台，支持实时处理、查询和计算。每个应用程序都可以发布与其业务部分相关的流，并以完全解耦的方式依赖其他流。

