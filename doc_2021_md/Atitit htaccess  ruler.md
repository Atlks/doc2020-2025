Atitit htaccess  ruler

【RewriteRule ^(.*)$ /blog/$1】重写规则，最重要的部分，意思是当上面的RewriteCond条件都满足的时候，将会执行此重写规则，^(.*)$是一个正则表达的 匹配，匹配的是当前请求的URL，^(.*)$意思是匹配当前URL任意字符，.表示任意单个字符，*表示匹配0次或N次（N>0），后面 /blog/$1是重写成分，意思是将前面匹配的字符重写成/blog/$1，这个$1表示反向匹配，引用的是前面第一个圆括号的成分，即^(.*)$中 的.* ，其实这儿将会出现一个问题，后面讨论。


如果后面还继续有语句的，就不应该加上最后的[L]，因为这是表示最后一条语句的意思


index.php / $ 1
在HTTP用语中，这是“ PATH_INFO”，给定url之类的
http://example.com/path/script.php/extra/stuff
然后服务器将调用/path/script.php，并将其/extra/stuff放入$_SERVER["PATH_INFO"]

