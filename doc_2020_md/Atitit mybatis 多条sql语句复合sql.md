Atitit mybatis 多条sql语句复合sql



mybatis xml 同时操作多条sql语句
2018年08月02日 17:32:51 _Weck2 阅读数 2280
 版权声明：转来转去都是原创 https://blog.csdn.net/qq_37012304/article/details/81364418
jdbc.url=jdbc:mysql://127.0.0.1:3306/test?useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true
jdbc.url加上标红字体



 <select id="warning_queryMlt" parameterType="Map" resultType="Map">
select taskname, place into @n, @pls from task_warning limit 1;
   select @n as n,@pls as pl;

  </select>



System.out.println( MybatisUtil.selectList("warning_queryMlt",null));

