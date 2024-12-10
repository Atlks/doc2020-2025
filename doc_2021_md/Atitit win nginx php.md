Atitit win nginx php


http set all cfg ... server is host cfg...

	server {


　开启php-cgi.exe
　　　　E:\self\soft\php-7.2.11/php-cgi.exe -b 127.0.0.1:9001 -c E:\self\soft\php-7.2.11/php.ini 
　　　　就是php目录下的 php-cgi.exe和php-ini文件，加上绝对路径，端口号要跟nginx的对上！
　　　　
　　　　这样子就是正常滴，别人为它傻了，怎么没反应。



C:\wamp\bin\php\php5.6.31\php-cgi.exe -b 127.0.0.1:9003 -c  C:\wamp\bin\php\php5.6.31\phpForApache.ini

Nginx whti php conn,by socket port
 fastcgi_pass 127.0.0.1:9003;
502 prblm
If only nginx no phpcgi start,,will   502 bad netgway  show in  nginx...



