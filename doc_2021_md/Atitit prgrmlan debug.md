Atitit prgrmlan debug 


#-------------调试node-inspector/eclipse /webstorm    
node.js本身支持调试(gdb也是,不好用.)，在语句前面加debugger指令就可以添加一个断点
在启动服务的时候添加debug 选项

node debug index.js


Php

C:\wamp\bin\php\php5.6.31\php.exe -dzend_extension=D:\wamp\bin\php\php5.6.31\zend_ext\php_xdebug-2.5.5-5.6-vc11.dll -dxdebug.remote_enable=1 -dxdebug.remote_mode=req -dxdebug.remote_port=9000 -dxdebug.remote_host=127.0.0.1 C:\Users\ATI\PhpstormProjects\apiprj\tmr.php


Just in  ide  ..  edit debug config ,,cfg interprxx cli php path,,add cfg debug cfg....


Or ,,use php.ini cfg debug....


Java的debug
