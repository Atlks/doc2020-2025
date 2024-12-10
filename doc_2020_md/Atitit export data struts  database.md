Atitit export data struts  database


182.16.50.115  root cjds1023123


1、导出数据库为dbname的表结构（其中用户名为root,密码为dbpasswd,生成的脚本名为db.sql）
    C:\Program1\bin\mysql\mysql5.7.19\bin\mysqldump.exe -uroot -pcjds1023123 -h 182.16.50.115   -d -R --triggers dev_kok_sport  >"C:\Users\Administrator\OneDrive\桌面\mysql script sql\dev_kok_sport_strutsU44.sql"
	
	
	
	参数说明：

-n: --no-create-db
-d: --no-data
-t: --no-create-info
-R: --routines Dump stored routines (functions and procedures)



----------------------------

其他有用的参数：

-E, --events        Dump events.

-R, --routines      Dump stored routines (functions and procedures).

--triggers          Dump triggers for each dumped table.



导入之前用

    SET FOREIGN_KEY_CHECKS=0; #禁用外键约束.

 
导完之后再用
    SET FOREIGN_KEY_CHECKS=1; #来启动外键约束.
查看当前FOREIGN_KEY_CHECKS的值可用如下命令

    SELECT  @@FOREIGN_KEY_CHECKS;


————————————————
版权声明：本文为CSDN博主「本木生」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/John_Chang11/article/details/52289991
