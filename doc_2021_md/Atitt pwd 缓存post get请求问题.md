Atitt pwd 缓存post get请求问题

默认请求只能保存get。。Post解决方案是把key作为url即可。。。这有不管get还是post都可以了。。


// jeig must beir page does-not-work-offline-error
this.addEventListener('fetch', function (event) {
    //   {ignoreVary: true}  igore head,,only need url match..
    //    caches.match(event.request)  caches.match(event.request, {ignoreVary: true})
    // it can be empty if you just want to get rid of that error
    //  caches.match(event.request.url) for post
    event.respondWith(
        caches.open(cacheStorageKey).then(cacheObj1 => {
            return caches.match(event.request.url)
                .then(function (response) {
                    if(event.request.method === "POST")
                    {

                    }
                    console.log(JSON.stringify( event.request)) //empty ,maybe to json
                        console.log('cache 缓存 match statue::', event.request.url, response);
                        //if no catch ,,resp is undefined
                        // Cache hit - return response
                        if (response) {
                            console.log('cache 缓存 exist:', event.request.url, response);
                            return response;
                        } else {
                            //not hit caech
                            return fetch(event.request).then(function (response) {
                                cacheObj1.put(event.request.url, response.clone());
                                return response;
                            });
                            //     var cache=window.applicationCache;
                            //     var cache=window.applicationCache;

                        }

                    }
                )
        })
    );
});

