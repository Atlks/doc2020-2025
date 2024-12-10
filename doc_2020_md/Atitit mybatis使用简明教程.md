Atitit mybatis使用简明教程

Mybatis.xml  配置文件

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration 
PUBLIC "-//mybatis.org//DTD Config 3.0//EN" 
"http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
<!--
    <properties resource="db.properties"></properties>
-->
   <settings>
   <!--   
      <setting name="defaultExecutorType" value="REUSE" />
      -->
      <setting name="defaultStatementTimeout" value="30000" />
   </settings>

 
   <environments default="mysql">
       
      <environment id="mysql">
         <transactionManager type="JDBC" ></transactionManager>
         <dataSource type="POOLED">
            <property name="driver" value="com.mysql.jdbc.Driver" />
            <property name="url" value="${mysql.url}" />
            <property name="username" value="${mysql.username}" />
            <property name="password" value="${mysql.password}" />
            <property name="poolMaximumIdleConnections" value="0" />
            <property name="poolMaximumActiveConnections" value="10" />
         </dataSource>
      </environment>
   </environments>

   <mappers>
    <mapper class="org.chwin.firefighting.apiserver.data.MybatisMapperCls"/>
      <mapper resource="datamp.xml" />
      
      <!--   
         <mapper resource="cn/freeteam/model/OperlogsMapper.xml"/>
         -->
   </mappers> 
</configuration>



Datamp.xml   mapper文件主要作用是分模块放sql语句

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper  PUBLIC "-//ibatis.apache.org//DTD Mapper 3.0//EN"  "http://ibatis.apache.org/dtd/ibatis-3-mapper.dtd">



<!-- todox o91 jeig nameespace will be   attach resultType zuchen yg  fullNameClass for map -->
<mapper namespace="/" >

    <select id="warning_query" parameterType="Map" resultType="Map">

         <![CDATA[
select * from yinhuanpaidanbiao
 ]]>

</mapper>


查询使用
package org.chwin.firefighting.apiserver.data;

import com.alibaba.fastjson.JSON;
import ognl.OgnlException;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;

import java.io.IOException;
import java.util.List;
import java.util.Map;

public class dataExecuter {

    public static void main(String[] args) throws IOException, OgnlException {


        SqlSessionFactory sqlSessionFactory = MybatisUtil. getSqlSessionFactory();

        SqlSession session = sqlSessionFactory.openSession(true);
        // api ��Ϊ[ openSession(boolean autoCommit) ]���ò���ֵ���������Ƹ� sqlSession �Ƿ��Զ��ύ��true��ʾ�Զ��ύ��false��ʾ���Զ��ύ[���޲εķ�������һ�£������Զ��ύ]

        List<Map>  rzt = session.selectList("warning_query",null);
        System.out.println(JSON.toJSONString(rzt, true));
    }
}

