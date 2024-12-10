Atitit  json_extract 读取json obj key方法

原理，搜索”key”, 搜索冒号和逗号之间对val..替换val对双引号






CREATE DEFINER=`root`@`%` FUNCTION `json_extract_obj`(
vs_json  VARCHAR(4096),#JSON数组字符串

in_KeyName VARCHAR(64)#键名
) RETURNS varchar(512) CHARSET utf8
BEGIN
DECLARE in_Index TINYINT DEFAULT 1;  #JSON对象序号，序号从1开始

 DECLARE vs_return VARCHAR(4096);
DECLARE vs_JsonArray, vs_Json, vs_KeyName VARCHAR(4096);
#declare vs_Json varchar(4096);
DECLARE vi_pos1, vi_pos2 SMALLINT UNSIGNED;
 
#写监控日志
#insert into dw.t_etl_log(sp_name, title, description) 
#values('dw.fn_Json_getKeyValue', '通过Json键名取键值', concat('in_JsonArray=', in_JsonArray));
# set in_JsonArray=CONCAT('[',in_JsonArray,']');
-- select in_JsonArray;
-- insert tmp_mm set log=vs_json;

 
SET vs_json = TRIM(vs_json);
SET vs_KeyName = TRIM(in_KeyName);
 
 
#去掉方括号
 
#取指定的JSON对象
 
 
 
SET vs_KeyName = CONCAT('"', vs_KeyName, '":');
SET vi_pos1 = INSTR(vs_json, vs_KeyName);
IF vi_pos1 > 0 THEN
		#如果键名存在
		SET vi_pos1 = vi_pos1 + CHAR_LENGTH(vs_KeyName);
		SET vi_pos2 = LOCATE(',', vs_json, vi_pos1);
		IF vi_pos2 = 0 THEN
				#最后一个元素没有','分隔符，也没有结束符'}'
				SET vi_pos2 = CHAR_LENGTH(vs_json) + 1;
		END IF;
		SET vs_return = REPLACE(MID(vs_json, vi_pos1, vi_pos2 - vi_pos1), '"', '');
END IF;
 
 
 
 
RETURN(vs_return);
END
