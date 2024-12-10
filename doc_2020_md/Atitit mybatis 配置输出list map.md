Atitit mybatis 配置输出list map


<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="IcolSetting">
	
	
	<insert   id="insert_datadic"  parameterType="Map"  >
		
			insert into datadic (key,val)values
		 
		(
		'${key}',
		'${val}'
	 
		 
		)
 
	</insert>
	
	<!--  hto d resultType sh single type-->
		<select   id="select_datadic"  parameterType="Map"   resultType="Map"  >
		
			select * from  datadic  where key='${key}'
		 
	 
 
	</select>
