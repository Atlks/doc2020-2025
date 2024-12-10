Atitt php add redis ext


Phpinfo 

PHP Version 5.6.31


Down redis dll

Cfg php.ini
extension_dir ="c:/phpenv/php5.6.31/ext/"


;redis
extension=php_igbinary.dll
extension=php_redis.dll


Reboot php
cd  c:\phpenv\Nginx1.15.11
start   nginx.exe
start  ../php5.6.31\php-cgi.exe -b 127.0.0.1:9000 -c  ../php5.6.31\phpForApache.ini

Check from php info
redis

