Atitt pwa net first cache 策略core code


//   {ignoreVary: true}  igore head,,only need url match..
//    caches.match(event.request)  caches.match(event.request, {ignoreVary: true})
// it can be empty if you just want to get rid of that error
//  caches.match(event.request.url) for post
// jeig must beir page does-not-work-offline-error
this.addEventListener('fetch', function (event) {

    //  console.log('fetchEvtFun( event.request.url---' + event.request.url);
    console.log("fetch.url:: " + event.request.url)


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

});



//die()...

var cacheStoK = 'stokey-7'

//   1 2 3 4  7 31  32   35 34
var cacheList_iniIntall = [

    "/",
    "/index.html",
    "/index.php/index/index.html",

    "/index.php/vod/search/by/time_add.html",
    "/index.php/vod/type/id/1.html",
    "/index.php/vod/type/id/2.html",
    "/index.php/vod/type/id/3.html",
    "/index.php/vod/type/id/4.html",

    "/index.php/vod/type/id/7.html",

    "/index.php/vod/type/id/31.html",
    "/index.php/vod/type/id/32.html",

    "/index.php/vod/type/id/34.html",
    "/index.php/vod/type/id/35.html",
    "/index.php/ajax/data.html?mid=1&page=1&limit=20&tid=&by=vod_time_add&order=&wd=&tag=",

    "/index.php/ajax/data.html?mid=1&page=1&limit=20&tid=1&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=2&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=3&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=4&by=&order=&wd=&tag=",

    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=7&by=&order=&wd=&tag=",

    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=31&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=32&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=33&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=34&by=&order=&wd=&tag=",
    "index.php/ajax/data.html?mid=1&page=1&limit=20&tid=35&by=&order=&wd=&tag="
]
bekcalst = [];
alwasNetList = [];
self.addEventListener('install', e => {
    console.log(" self.install evt....")
    e.waitUntil(
        caches.open(cacheStoK)
            .then(cache => cache.addAll(cacheList_iniIntall))
            .then(() => self.skipWaiting())
    )
    console.log(" self.install finish ..")
});

String.prototype.startWith = function (str) {
    var reg = new RegExp("^" + str);
    return reg.test(this);
}

//测试ok，直接使用str.endWith("abc")方式调用即可
//有bug  ，如果包含特殊符号，比如url
String.prototype.endWith = function (str) {
    var reg = new RegExp(str + "$");
    return reg.test(this);
}

function endWith(str, suffix) {
    return str.indexOf(suffix, str.length - suffix.length) !== -1;
}
function startWithx(str, suffix) {
    return  false;
}


function endWithx(url2, needX) {
    var url = url2;
    var arr = needX.split(",");
    for (const v of arr) {
        if (url.endWith(v))
            return true;
    }
    return false;
}




//   {ignoreVary: true}  igore head,,only need url match..
//    caches.match(event.request)  caches.match(event.request, {ignoreVary: true})
// it can be empty if you just want to get rid of that error
//  caches.match(event.request.url) for post
// jeig must beir page does-not-work-offline-error
this.addEventListener('fetch', function (event) {

    //  console.log('fetchEvtFun( event.request.url---' + event.request.url);
    console.log("fetch.url:: " + event.request.url)


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

});


// hamyar d not must
/**
 * 错误监控
 SW 运行在 worker 线程里，其抛出的错误在页面是捕捉不到的，因此需要在 SW 里引入错误监控。（感谢题叶老师提供错误监控 SDK 的 SW 版本）


 */
/**
 * self.addEventListener('error', event => {
    // 上报错误信息
    // 常用的属性：
    // event.message
    // event.filename
    // event.lineno
    // event.colno
    // event.error.stack
    console.log('sw error lstnr:' + JSON.stringify(event) );
})
 self.addEventListener('unhandledrejection', event => {
    // 上报错误信息
    // 常用的属性：
    // event.reason
    console.log('sw unhandledrejection lstnr:' + JSON.stringify(event));
})
 */


/** 一般动态不存缓存里面去取   部分可以cache
 * self.addEventListener('fetch', function(event) {
    event.respondWith(
        caches.match(event.request)
            .then(function(response) {
                    // Cache hit - return response
                    if (response) {
                        return response;
                    }
                    return fetch(event.request);
                }
            )
    );
});
 */


function randomNotification() {
    var randomItem = Math.floor(Math.random() * games.length);
    var notifTitle = games[randomItem].name;
    var notifBody = 'Created by ' + games[randomItem].author + '.';
    var notifImg = 'data/img/' + games[randomItem].slug + '.jpg';
    var options = {
        body: notifBody,
        icon: notifImg
    }
    var notif = new Notification(notifTitle, options);
    setTimeout(randomNotification, 30000);
}
function endWith_cachelist(url, cacheList) {
    //   var url = url2;
//    var arr = needX.split(",");
    for (const cached_url of cacheList) {
        // console.log('url.endWith(cached_url):' + url + "***************" + cached_url)
        // console.log(url)
        // console.log(cached_url)
        if (endWith(url, cached_url)) {
            //  console.log("compRzt   true")

            return true;
        } else {
            //  console.log("compRzt   false")
        }
        //  console.log('url.endWith(cached_url)==> ( '+url+":"+ cached_url  +  " ,rzt:"+);
    }
    return false;
}

