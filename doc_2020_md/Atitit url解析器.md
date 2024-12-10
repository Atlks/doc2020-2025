Atitit url解析器




Url标准

数组中可能的键有以下几种：
scheme - 如 http
host
port
user
pass
path
query - 在问号 ? 之后
fragment - 在散列符号 # 之后

nodejs获取当前url和url参数值
转载thinkKoa 最后发布于2016-10-21 00:42:24 阅读数 3019  收藏
展开
php中可以通过post or get 获取到url中的参数值，最近接触了node那么在nodejs里是怎么做的呢，上代码了！
//需要使用的模块 http   url
当前url   http://localhost:8888/select?aa=001&bb=002
var http = require('http');
var URL = require('url');
http.createServer(function(req, res){
   var arg = url.parse(req.url).query;  //方法一arg => aa=001&bb=002
   var arg = url.parse(req.url, true).query;  //方法二arg => { aa: '001', bb: '002' }
   console.log(arg.aa);//返回001
   console.log(arg.bb);//返回002
   //然后就可以根据所得到的数据处理了

}).listen(8888);//建立服务器并监听端口

获取特定url参数值
var testUrl =  'http://localhost:8888/select?aa=001&bb=002';
var p = URL.parse(testUrl); 
console.log(p.href); //取到的值是：http://localhost:8888/select?aa=001&bb=002
console.log(p.protocol); //取到的值是：http: 
console.log( p.hostname);//取到的值是：locahost
console.log(p.host);//取到的值是：localhost:8888
console.log(p.port);//取到的值是：8888
console.log(p.path);//取到的值是：/select?aa=001&bb=002
console.log(p.hash);//取到的值是：null 
console.log(p.query);// 取到的值是：aa=001
在此值得注意的是当语句 是 var p = URL.parse(testUrl, true) 时,p.query则返回的是如：{aa:'001'}这样的对象， 直接打印p.query则返回 [object Object]，这时我们可以这样 写： console.log(p.query.aa); //取到的值是：001
console.log( p.pathname);//取到的值是：/select

下面附上js的获取方法：

当前URL   http://mj_0203.0fees.net/index.php?aa=001&bb=002
document.location:        http://mj_0203.0fees.net/index.php?aa=001&bb=002
document.URL:             http://mj_0203.0fees.net/index.php?aa=001&bb=002
document.location.href:   http://mj_0203.0fees.net/index.php?aa=001&bb=002
self.location.href:       http://mj_0203.0fees.net/index.php?aa=001&bb=002
top.location.href:        http://mj_0203.0fees.net/index.php?aa=001&bb=002
parent.document.location: http://mj_0203.0fees.net/index.php?aa=001&bb=002
top.location.hostname:    mj_0203.0fees.net
location.hostname:        mj_0203.0fees.net

php的两个内置函数就可以顺利完成，即parse_url和parse_str函数
通过php获取了当前url，如果需要提取url中的参数的话该如何操作呢？这个过程其实挺简单，使用php的两个内置函数就可以顺利完成，即parse_url和parse_str函数。下面将对这两个函数做简要说明以及用示例说明如何提取url中的参数。
（1）parse_url (PHP 4, PHP 5) — 解析 URL，返回其组成部分，函数原型如下：
mixed parse_url ( string $url [, int $component = -1 ] )
本函数解析一个 URL 并返回一个关联数组，包含在 URL 中出现的各种组成部分。
本函数不是用来验证给定 URL 的合法性的，只是将其分解为下面列出的部分。不完整的 URL 也被接受，parse_url() 会尝试尽量正确地将其解析。
参数说明
url 要解析的 URL。无效字符将使用 _ 来替换。
component 指定 PHP_URL_SCHEME、 PHP_URL_HOST、 PHP_URL_PORT、 PHP_URL_USER、 PHP_URL_PASS、 PHP_URL_PATH、 PHP_URL_QUERY 或 PHP_URL_FRAGMENT 的其中一个来获取 URL 中指定的部分的 string。 （除了指定为 PHP_URL_PORT 后，将返回一个 integer 的值）。
返回值
对严重不合格的 URL，parse_url() 可能会返回 FALSE。
如果省略了 component 参数，将返回一个关联数组 array，在目前至少会有一个元素在该数组中。数组中可能的键有以下几种：
scheme - 如 http
host
port
user
pass
path
query - 在问号 ? 之后
fragment - 在散列符号 # 之后
类似  mysql url
