Php cant dbg use xdbg   port 9000 cant conn


Show ext

Php -m    cant find xdbg...

So use phpstudy delt xdebg ext,then add again..     -m agian ,,can see..

Cfg ini xdbg cfg ...


xdebug.remote_enable=on
xdebug.remote_host=localhost
xdebug.remote_port=9009
xdebug.remote_handler=dbgp



So can conn ide 9009 port


Bcs 9000 alslo use in nginx..



C:\phpstudy_pro\Extensions\php\php8.0.2nts\php.exe -dxdebug.remote_enable=1 -dxdebug.remote_mode=req -dxdebug.remote_port=9009 -dxdebug.remote_host=127.0.0.1 -dxdebug.mode=debug -dxdebug.client_port=9009 -dxdebug.client_host=127.0.0.1 C:\modyfing\jbbot\app\common\asyn_timer_tpCmd.php

