Atitit mysql存储过程问题


声明变量Declare语句注意点：

Declare语句通常用来声明本地变量、游标、条件或者handler


Declare语句只允许出现在BEGIN...END语句中而且必须出现在第一行


Declare的顺序也有要求，通常是先声明本地变量，再是游标，然后是条件和handler

自定义变量命名注意点：
自定义变量的名称不要和游标的结果集字段名一样。若相同会出现游标给变量赋值无效的情况。
临时表只在当前连接可见，当关闭连接时，Mysql会自动删除表并释放所有空间。因此在不同的连接中可以创建同名的临时表，并且操作属于本连接的临时表。



循环fetch多个对问题 使用loop模式代替 while  



declare cr cursor for select Name,StgId from StgSummary ORDER BY StgId desc LIMIT 3;
declare continue handler for not found set done = 1;
 
-- 打开游标
open cr;
testLoop:LOOP
    -- 获取结果
    fetch cr into c_stgName,c_stgId;
    IF done = 1 THEN
        LEAVE testLoop; 
    END IF; 
     
   
  SELECT c_stgName,c_stgId;
     
END LOOP testLoop;
-- 关闭游标
close cr;

