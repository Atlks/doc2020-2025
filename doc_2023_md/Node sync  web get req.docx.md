Node sync  web get req


：Node的版本>=8.0.0 为了使用 Async / Await PS: 这里加入auth 字段是为了需要用户名和密码登录的应用的请求 ，比如rabbitmq ,不需要登录的页面可以去掉这个参数。

"node-fetch
    async http_get239(url) {
        console.log(url);
        const fetch = require('node-fetch');

        //  import fetch from "node-fetch"; //es6 mode
        const res = await fetch(url);
        const headerDate = res.headers && res.headers.get('date') ? res.headers.get('date') : 'no response date';
        console.log('___Status Code:', res.status);
        console.log('___+Date in Response header:', headerDate);

        const r = await res.text();
        // await res.json();    require('node-fetch')(url).text()
        return r;

}


第一种
使用原生模块 util , 利用其 promisify API ， 代码示例如下：

 
