Atitit mysql存储过程异常处理



MySQL存储过程的异常处理
阅读目录：存储过程的异常处理
定义异常处理
单一异常处理程序
　　　　continue
　　　　exit
多个异常处理程序
　　　　关于错误编号和SQLSTATE码
　　　　使用3个处理程序
　　　　忽略某一异常的处理
异常处理的命名
异常传播



五、异常传播
　　在嵌套块的情况下，内部块中发生异常了，首先由本块的异常处理程序来处理，如果本块没有处理，则由外部块的异常处理程序来处理。
mysql> DELIMITER $$
mysql> CREATE  PROCEDURE small_mistake6()  
    -> BEGIN    
    -> 　　DECLARE CONTINUE HANDLER FOR SQLSTATE '23000' 
    -> 　　SET @processed = 100;  
    ->
    -> 　　BEGIN      
    -> 　　　　DECLARE CONTINUE HANDLER FOR SQLSTATE '21000' 
    -> 　　　　SET @processed = 200;    
    -> 　　　　INSERT INTO TEAMS VALUES(2,27,'third');   
    -> 　　　　set @test=123321;  
    ->    END;
    -> END$$
mysql> DELIMITER ;
mysql> call small_mistake6;
mysql> select @processed,@test;+------------+--------+
| @processed | @test |
+------------+--------+
| 300 | 123321 |
+------------+--------+
解析：@processed=100说明内部块里的异常传播到了外部块，交由外部块的异常处理程序进行的处理。
墙裂建议：
　　当有多层begin end的时候，每层都应该有自己完善的异常处理，做到：自己的异常，自己这层去处理。

