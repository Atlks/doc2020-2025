Atitit deadlockchk  .sp  存储过程与记录集循环


BEGIN
	#Routine body goes here...


-- 定义变量
	DECLARE s int DEFAULT 0;
	DECLARE pid int;
	DECLARE sec int;
	-- 定义游标，并将sql结果集赋值到游标中
	DECLARE CURSOR11 CURSOR FOR select trx_mysql_thread_id,now()-trx_started as secs from information_schema.innodb_trx;
	-- 声明当游标遍历完后将标志变量置成某个值
	DECLARE CONTINUE HANDLER FOR NOT FOUND SET @exitx=1;
	-- 打开游标
	open CURSOR11;
		-- 将游标中的值赋值给变量，注意：变量名不要和返回的列名同名，变量顺序要和sql结果列的顺序一致
   --  set @pid=0; 
   --   set @sec=0;
	 	fetch CURSOR11 into pid,sec;
		-- 当s不等于1，也就是未遍历完时，会一直循环
		while pid>0 do

				BEGIN
					  		-- DECLARE CONTINUE HANDLER FOR NOT FOUND SET s=1;
								-- 执行业务逻辑
								if sec>15 then
                    	insert logx set log= CONCAT(' will kill pid:',pid);
										kill pid;
										insert logx set log= CONCAT(' kill pid:',pid);
								end if ;
						     
								-- 将游标中的值再赋值给变量，供下次循环使用
								fetch CURSOR11 into pid,sec;
							-- 当s等于1时表明遍历以完成，退出循环
				end ;

		end while;
	-- 关闭游标
	close CURSOR11;


END
