Atiti. Php Laravel 5.1 环境搭建以及  error 排除



1. php_5.6.11_apache2.4	1
1.1. Httpd。Conf增加以下配置，添加php支持	1
1.2. 修改apache位置与项目位置以及权限	1
1.3. 修改php。Ini。增加mbstring，openssl，mysql，rewriting的支持 extension_dir = "C:\wamp\php_5.6.11_XiaZaiBa\ext"	2
2. 错误排除	2
2.1. laravel 5.1 unexpected T_STRING Illuminate Contracts—Http Kernel lass	2
2.2. httpd.exe: Syntax error on line 531 of C:/Apache24/conf/httpd.conf: Cannot load c:/php56/php5apache2_4.dll into server: \xd5\xd2\xb2\xbb\xb5\xbd\xd6\xb8\xb6\xa8\xb5\xc4\xc4\xa3\xbf\xe9\xa1\xa3	3
2.3. started.httpd:Syntax error on line 60 of D:/apache2/conf/httpd.conf:Cannot load D:/apache2/modules/mod_actions.so into server:\xd5\xd2\xb2\xbb\xb5\xbd\xd6\xb8\xb6\xa8\xb5\xc4\xa3\xbf\xe9\xa1\xa3	3
2.4. Fatal error: Call to undefined function Illuminate\Foundation\Bootstrap\mb_internal_encoding	4
2.5. apache documentroot指向htcdoc之外提示403错误的解决方法	5
2.6. 开启框架调试模式	7
3. 配置Redis	7
3.1.1. redis windows官方下载|Redis for Windows下载 2.6.13 稳定版 - ...	8
3.2. 数据库配置	8
4. --fihi是、	9

 php_5.6.11_apache2.4
Httpd。Conf增加以下配置，添加php支持
LoadModule php5_module  "c:/wamp/php_5.6.11_XiaZaiBa/php5apache2_4.dll"
AddType application/x-httpd-php .php

PHPIniDir "C:\wamp\php_5.6.11_XiaZaiBa"

修改apache位置与项目位置以及权限
Define SRVROOT "/Apache24"
DocumentRoot  "${SRVROOT}/htdocs/eform/public" 
<Directory "${SRVROOT}/htdocs/eform/public">
    AllowOverride all
   Require all granted
</Directory>
还要修改Apache24\conf\extra\httpd-vhosts.conf

<VirtualHost _default_:80>
#DocumentRoot "${SRVROOT}/htdocs"
DocumentRoot "d:/www"
#ServerName www.example.com:80
</VirtualHost>
作者::  ★(attilax)>>>   绰号:老哇的爪子 （ 全名：：Attilax Akbar Al Rapanui 阿提拉克斯 阿克巴 阿尔 拉帕努伊 ） 汉字名：ail，  EMAIL:1466519819@qq.com
转载请注明来源： http://blog.csdn.net/attilax

修改php。Ini。增加mbstring，openssl，mysql，rewriting的支持
extension_dir = "C:\wamp\php_5.6.11_XiaZaiBa\ext"
- PHP >= 5.5.9 - OpenSSL PHP 扩展 - PDO PHP 扩展 - Mbstring PHP 扩展 - Tokenizer PHP 扩展

错误排除
laravel 5.1 unexpected T_STRING Illuminate Contracts—Http Kernel lass

Parse error: syntax error, unexpected T_STRING in C:\wamp\www\eform\public\index.php on line 50

$kernel = $app->make(Illuminate\Contracts\Http\Kernel::class);//This is line 50
the ::class is only supported since PHP 5.5
Also you must have mistakingly installed laravel 5.1+ because that's the only version to require php 5.5+


Laravel 5.1 requires PHP 5.5.9 
解决。下载  php_5.6.11_XiaZaiBa
里面需要php5apache2_4.dl，需要apache2.4

在运行Apache24/bin目录下运行httpd.exe -t时，如果出现如下错误提示信息：
httpd.exe: Syntax error on line 531 of C:/Apache24/conf/httpd.conf: Cannot load c:/php56/php5apache2_4.dll into server: \xd5\xd2\xb2\xbb\xb5\xbd\xd6\xb8\xb6\xa8\xb5\xc4\xc4\xa3\xbf\xe9\xa1\xa3

是由于php5apache2_4.dll动态链接库文件的版本与当前的php版本或Apache版本不匹配。32位64位。
通过loadpe查看 php5apache2_4.dll信息，是32位的，下载32为的apathc2.4

started.httpd:Syntax error on line 60 of D:/apache2/conf/httpd.conf:Cannot load D:/apache2/modules/mod_actions.so into server:\xd5\xd2\xb2\xbb\xb5\xbd\xd6\xb8\xb6\xa8\xb5\xc4\xa3\xbf\xe9\xa1\xa3
errors reported here must be corrected before service can be 
原因:
我也遇到了这个问题，确实是由于配置ServerRoot不当导致的，仔细看了一下conf文件里面有一个说明ServerRoot: The top of the directory tree under which the server‘s等等，应该是Apache文件夹只能放在磁盘根目录下，不能放在文件夹中，不然会造成非目录错误或楼主的问题。

Define SRVROOT "/Apache24"
ServerRoot "${SRVROOT}"
将${SRVROOT} 改成你的apache安装目录
比如 我的安装目录是 在F盘中 所以改后是这样的
Define SRVROOT "/Apache24"
ServerRoot "F:/Apache24"

Fatal error: Call to undefined function Illuminate\Foundation\Bootstrap\mb_internal_encoding



PHPIniDir "D:\wamp\bin\php\php5.4.3"

extension_dir = "ext"   cantloasd ,use   “./ext” hesh cant ..
extension_dir = "C:\wamp\php_5.6.11_XiaZaiBa\ext"   zash ok le ..

 首先用phpinfo测试页面看一下有没有装载mbstring, 
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

开启框架调试模式
Config、app.php

    'debug' => true,
//	env('APP_DEBUG', false),
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

数据库配置
PHP数组，该配置文件提供了各种数据库可能用到的配置。connections 里包含了数据库配置。修改'default' => 'mysql',参数可以选择需要使用的数据库。
'mysql' => [
    'driver'    => 'mysql',
    'host'      => env('DB_HOST', 'localhost'),
    'database'  => env('DB_DATABASE', 'forge'),
    'username'  => env('DB_USERNAME', 'forge'),
    'password'  => env('DB_PASSWORD', ''),
    'charset'   => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix'    => '',
    'strict'    => false,
],
上面是默认的MySQL配置项，'host' => env('DB_HOST', 'localhost'),中env()方法就是读取.env文件中的配置项，它的第二个参数是默认值。当然也可以通过'password' => 'password',直接配置，但是如果我们把项目存放到GitHub上时，这么做显然是不安全的。可以通过读取.env配置文件中的配置，然后把.env配置文件设置为不提交来解决，这也是通过.env配置文件来配置的一个好处。
打开项目根目录下的.gitignore文件，可以看到.env默认是不会被提交的。


参考
[Laravel 5 教程学习笔记] 六、环境与配置 _ Specs' Blog-就爱PHP.html


--fihi是、


