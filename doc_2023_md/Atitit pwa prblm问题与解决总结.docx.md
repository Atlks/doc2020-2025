Atitit pwa prblm问题与解决总结


Prblm
不出现安装图标
可在chrome,开发工具，app里面查看，知道满足安装条件。。

无法使用缓存 API 缓存 POST 请求

 个回答
积极的最老的投票
38

您无法使用缓存 API 缓存 POST 请求。请参阅https://w3c.github.io/ServiceWorker/#cache-put（第 4 点）。
规范存储库中有相关讨论：https : //github.com/slightlyoff/ServiceWorker/issues/693
一个有趣的解决方案是 ServiceWorker Cookbook 中提出 的解决方案：https : //serviceworke.rs/request-deferrer.html基本上，该解决方案将请求序列化到 IndexedDB。




浏览器兼容性？？


