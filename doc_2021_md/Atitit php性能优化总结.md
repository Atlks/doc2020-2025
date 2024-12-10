Atitit php性能优化总结

开启opcache ，
貌似对feb数列没啥影响，网上说可能对tps有影响四五倍的样子。。

 开启下opcache  看怎么样，网上有的说不错

 我这边是这样

 [opcache]
; opcache documentation http://fr2.php.net/manual/fr/opcache.installation.php   ..
zend_extension ="d:/wamp/bin/php/php7.1.9/ext/php_opcache.dll"
; Determines if Zend OPCache is enabled
opcache.enable=1

开启性能日志xdebug.profiler


[xdebug]
zend_extension ="d:/wamp/bin/php/php7.1.9/zend_ext/php_xdebug-2.5.5-7.1-vc14.dll"

xdebug.remote_enable = off
xdebug.profiler_enable = on
xdebug.profiler_enable_trigger = Off
xdebug.profiler_output_name = cachegrind.out.%t.%p
xdebug.profiler_output_dir ="d:/wamp/tmp"
xdebug.show_local_vars=0


Qcachegrind 是百分比显示的，比较大  18M
wincachegrind-1.1.zip 比较少 1M大小
