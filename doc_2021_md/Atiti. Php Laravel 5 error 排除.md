Atiti. Php Laravel 5 error 排除


Fatal error: Call to undefined function Illuminate\Foundation\Bootstrap\mb_internal_encoding



PHPIniDir "D:\wamp\bin\php\php5.4.3"

extension_dir = "ext"   cantloasd ,use   “./ext” hesh cant ..
extension_dir = "C:\wamp\php_5.6.11_XiaZaiBa\ext"   zash ok le ..

 首先用phpinfo测试页面看一下有没有装载mbstring,如果没有,尝试将php_mbstring.dll复制到%windows%目...

mbstring



apache documentroot指向htcdoc之外提示403错误的解决方法

后来发现，原来又是Apache没配置 好，是apache的mod_authz_host模块在起控制作用。 
1.如果不启用vhosts 
只需修改 httpd.conf 
默认Directory节如下，注意红色部分，表示目录/usr/local/apache/htdocs允许所有 主机访问

一、访问控制
在Apache2.2版本中，访问控制是基于客户端的主机名、IP地址以及客户端请求中的其他特征，使用Order(排序), Allow(允许), Deny(拒绝),Satisfy(满足)指令来实现。
在Apache2.4版本中，使用mod_authz_host这个新的模块，来实现访问控制，其他授权检查也以同样的方式来完成。旧的访问控制语句应当被新的授权认证机制所取代，即便Apache已经提供了mod_access_compat这一新模块来兼容旧语句。
这里有一些实例，用新方法取代旧语句实现相同的访问控制
：常见访问控制指令
复制代码代码如下:

Require all granted #允许所有
Require all denied #拒绝所有
Require env env-var [env-var] ... #允许，匹配环境变量中任意一个
Require method http-method [http-method] ... #允许，特定的HTTP方法
Require expr expression #允许，表达式为true
Require user userid [ userid ] ... #允许，特定用户
Require group group-name [group-name] ... #允许，特定用户组
Require valid-user # #允许，有效用户
Require ip 10 172.20 192.168.2 #允许 特定IP

在国外的网站上搜了好长时间终于找到问题了。
还要修改Apache24\conf\extra\httpd-vhosts.conf

<VirtualHost _default_:80>
#DocumentRoot "${SRVROOT}/htdocs"
DocumentRoot "d:/www"
#ServerName www.example.com:80
</VirtualHost>

希望对后来者有帮助



配置Redis
前面我们已经提到Redis可以用作主数据库，所以Laravel中Redis的配置信息位于config/database.php 中：
'redis' => [  'cluster' => false,  'default' => [    'host' => '127.0.0.1',    'port' => 6379,    'database' => 0,  ],
],
另外Redis如果是作为缓存工具，还需要在 config/cache.php 配置 redis 选项：
'redis' => [
    'driver' => 'redis',
    'connection' => 'default',
],
这里的 connection 对应 config/database 中 redis 的默认主机 default 配置。
完成上述配置之后我们就可以在应用代码中使用Redis进行数据存取了。
redis windows官方下载|Redis for Windows下载 2.6.13 稳定版 - ...
下载地址   大小: 1.13 MB   更新时间: 2013-06-13
 redis是一个key-value存储系统.和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)...
www.newasp.net/soft/67...  - 百度快照

