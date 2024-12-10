Atitit mybatis返回多个数据集总结






配置resultMap  ok

Mapper。xml
<mapper namespace="/" >

    <resultMap id="rm" type="map">    </resultMap>
    <resultMap id="rm2" type="map"></resultMap>
    <select id="retMltRzt" parameterType="map" resultMap="rm,rm2">
select 'ok';select  'msg' ; select 'rzt';
    </select>

调用代码
    SqlSession session = sqlSessionFactory.openSession(true);
List<List<Map>>  li=   session.selectList("retMltRzt",null);
   // session.select("retMltRzt",null,new MyResultHandler());
    System.out.println(JSON.toJSONString(li));
注意 多个结果集要定义多个resultMap接收 ，不然最后的结果集就丢失了
ref
配置handleResult接受，但是只有第一个select语句的结果

(9+条消息)mybatis调用mysql存储过程（返回参数，单结果集，多结果集） - 阿瑟与非 - CSDN博客.html

