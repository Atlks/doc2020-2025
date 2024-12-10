Atitit pwa prblm问题与解决总结

Prblm
没哟ssl https
Localhost 可以直接使用http测试
不出现安装图标
可在chrome,开发工具，app里面查看，知道满足安装条件。。

无法使用缓存 API 缓存 POST 请求

 积极的最老的投票
38

您无法使用缓存 API 缓存 POST 请求。请参阅https://w3c.github.io/ServiceWorker/#cache-put（第 4 点）。
规范存储库中有相关讨论：https : //github.com/slightlyoff/ServiceWorker/issues/693
一个有趣的解决方案是 ServiceWorker Cookbook 中提出 的解决方案：https : //serviceworke.rs/request-deferrer.html基本上，该解决方案将请求序列化到 IndexedDB。

Cache key 使用url模式+使用net first策略。。
也可以把post参数拼接起来作为url。。。Key

实现离线app
Net first策略。
//def tsalue ,,net first
return event.respondWith(
    fetch(event.request).then(response =>
            caches.open(cacheStoK).then(cacheObj1 =>
            {
                //must cache then ret,,beir..asyn said reposen already use
                cacheObj1.put(event.request.url, response.clone());
                return response;
            })
    ).catch(() => {
        return caches.match(event.request.url);
    })
    //fetch end
);
//end rspwz

调试pwa
Atitit pwa调试渐进式 Web 应用程 v2.docx
也可以是console控制台输出
浏览器兼容性？？

// todo fetchAwasysList
if( startWithx( event.request.url,alwasNetList)){
    console.log(" startWithx ", event.request.url)
    return fetch(event.request); //fet from url..
}
else if (event.request.url.startWith('chrome-extension')) {
    //need jar,,yva sh exteng.png file ,,alway fetch
    console.log(" chrome-extension ,not need cache ,fetch alwas ")
    return fetch(event.request); //fet from url..
} else {
    //fet alway block
    /// console.log(" not static file,  ,alswa fetch new" + event.request.url);
    //  return fetch(event.request); //fet from url..

}

