Atitit 定时刷新调度方法总结

尽可能利用系统现有，免安装其他
脚本/数据模式随时修改
跨平台更好
Linux crontab 最简单
crontab  -e 编辑调度任务，进入vi命令模式， I进入编辑状态，vi，， esc 退出编辑状态，回到vi命令模式。。  :wq保存


* * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "new com.kok.sport.utils.mockdata.unitRecentlyV2().test__Football_matchStatScoreFlush()"

Java默认只能直接执行class文件的main方法，其他方法需要使用方法运使用行期分发。。使 用spring的spel执行具体方法 。。Php python node脚本可以直接执行文件
MethodRunner参数命令包含空格使用双引号括起来。。如包含双引号，使用俩个双引号转义。。。

Mysql event  （仅sql）
貌似只能一行sql  ，如果多行sql 可以写出sp调用
缺点是不能直接调用程序语言
Mysql event  扩展+Linux crontab
增强扩展让其可以执行宿主语言
扩展运行
  * * * * * java -cp  /target/classes:/data/depl/BOOT-INF/lib/*:/data/deployer2/sport-service/*  com.kok.sport.utils.ql.MethodRunner "T(com.kok.sport.utils.db.EventMysqlExt).main(null)"



Mysql event里面
 insert sys_event set event_def='new com.kok.sport.utils.mockdata.unitRecentlyV2().Live_Match_list_stat_score_today()',event_name='Live_Match_list_stat_score_today'

将要执行的宿主语言代码写进去，spring spel格式


其他
脚本类nodejs python timer 跨平台
其他系统
