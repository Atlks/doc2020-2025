苹果cms 新部署后采集分类丢失的问题

因为苹果cms的部分配置是放在文件里面的，，所以如果新部署版本，常见的使用replace模式的化，就会造成采集分类配置的丢失


解决方法，使用meger融合模式去部署

使用git pull部署。。
先备份配置文件，部署后恢复。
使用对比工具 byound compare等去对比融合。。。

涉及到的配置文件清单
/application/extra/bind.php    分类绑定配置文件
/application/extra/captcha.php
/application/extra/domain.php
/application/extra/maccms.php
/application/extra/queue.php
1:  /application/extra/queue.php
 	行 9: /application/extra/timming.php
	 	行 17: /application/extra/version.php
	 
	行 25: /application/extra/voddowner.php
 	行 33: /application/extra/vodplayer.php
 	行 41: /application/extra/vodserver.php 
