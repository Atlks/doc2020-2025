Atitit 持久化日志 数据自动覆盖方式

保留每天持久化方式，时间字符串为hhmmss

保留每小时持久化，时间字符串为mmss

检测删除过久的表  
CREATE DEFINER=`root`@`%` PROCEDURE `持久化tmp_log_zmhz`()
BEGIN

--  DROP TABLE IF EXISTS `ssc_play_pl`;
set @tab=concat('cp3.tmp_log_zmhz_disk_',DATE_FORMAT(NOW(),'%i_%s'));
select  @tab;
set @sql=CONCAT('drop table IF EXISTS ',@tab);
select @sql;
 PREPARE INSERT_SQL FROM @sql;
		EXECUTE INSERT_SQL; 

set @sql='';
set @sql=CONCAT('create table ',@tab,'   select * from   cp.tmp_log_zmhz_memory');
select @sql;
 PREPARE INSERT_SQL2 FROM @sql;
		EXECUTE INSERT_SQL2; 

END


Code 持久化tmp_log_zmh



CREATE DEFINER=`root`@`%` PROCEDURE `持久化tmp_log_zmhz`()
BEGIN



set @mint=DATE_FORMAT(NOW(),'%i');select @mint;
	 if @mint<10 then 
			set @mint= @mint+60;
		end if;
set @del_min=@mint-10;  

	 if @del_min<10 then 
			set @del_min=CONCAT('0',@del_min);
		end if;
	select @del_min;	
	
	
	set @sec=0;
while @sec<60 do 
    if @sec<10 then 
			set @sec=CONCAT('0',@sec);
		end if;	
		
		
		set @tab=concat('cp3.tmp_log_zmhz_disk_',@del_min,'_',@sec);
	select  @tab;
	set @sql=CONCAT('drop table IF EXISTS ',@tab);
	select @sql;
	 PREPARE INSERT_SQL FROM @sql;
			EXECUTE INSERT_SQL; 
			
			
			set @sec=@sec+1;

end while;

-- select * from xxx;

--  DROP TABLE IF EXISTS `ssc_play_pl`;
set @tab=concat('cp3.tmp_log_zmhz_disk_',DATE_FORMAT(NOW(),'%i_%s'));
select  @tab;
set @sql=CONCAT('drop table IF EXISTS ',@tab);
select @sql;
 PREPARE INSERT_SQL FROM @sql;
		EXECUTE INSERT_SQL; 

set @sql='';
set @sql=CONCAT('create table ',@tab,'   select * from   cp.tmp_log_zmhz_memory');
select @sql;
 PREPARE INSERT_SQL2 FROM @sql;
		EXECUTE INSERT_SQL2; 

END
