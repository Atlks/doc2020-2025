Atitit mybatis mapper exe sql  



	@Test
	public void test() {
 
		SqlSession sess=	sqlSessionFactory.openSession(true);
	Object o=	sess.selectList("nmspc.query","select 1 as t");
	System.out.println(o);
		
	}

parameterType="java.lang.String"

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="nmspc">
   

 <select id="query"  resultType="Map">
       ${_parameter} 
    </select>
</mapper>


 <!-- mybatis动态sql的两个内置参数
           不只是方法传递过来的参数可以被用来判断，取值
       mybatis默认还有两个内置参数
           _parameter:代表整个参数
                                      单个参数：_parameter就是这个参数
                                      多个参数：参数会被封装为一个map:_parameter就是代表这个map             
           _databaseId:如果配置了databaseIdProvider标签
                _databaseId 就是代表当前数据库的别名Oracle
      -->

  where ename=#{_parameter.eName}  
