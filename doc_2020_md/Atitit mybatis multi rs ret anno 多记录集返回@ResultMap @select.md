Atitit mybatis multi rs ret anno 多记录集返回@ResultMap @select


allowMultiQueries 和sp模式
一种模式是使用allowMultiQueries=true
一种是使用 sp 返回多个

test

	@Test
	public void querySqlMultiRs2() throws Exception {
		
		//querySqlMultiRs  select 2;
		
	List li=	MybatisUtil.getMybatisMapper().querySqlMultiRs("call sp_multitab" );
	System.out.println(li);
	}
	
	
	@Test
	public void querySqlMultiRs() throws Exception {
		
		//querySqlMultiRs  select 2;
		
	List li=	MybatisUtil.getMybatisMapper().querySqlMultiRs("select 1;select 2;" );
	System.out.println(li);
	}
	

MybatisMapper 
@Mapper
public interface MybatisMapper {
 	
	@Select("${sql_intag}" )
@ResultMap({"/.rm","/.rm2","/.rm3","/.rm4","/.rm5"})
	public List<List<LinkedHashMap>> querySqlMultiRs(@Param("sql_intag") String sql);



 /mapper/rm.xml

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="/">
    <!-- 自定义返回结果集 -->
    
    
      <resultMap id="rm" type="map">

    </resultMap>
    <resultMap id="rm2" type="map">

</resultMap>
  <resultMap id="rm3" type="map">

</resultMap>
  <resultMap id="rm4" type="map">

</resultMap>
  <resultMap id="rm5" type="map">

</resultMap>

Rf
Atitit mybatis 多条sql语句复合sql
Atitit mybatis返回多个数据集总结v2.docx

