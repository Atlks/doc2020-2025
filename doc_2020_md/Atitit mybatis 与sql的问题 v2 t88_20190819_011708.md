Atitit mybatis 与sql的问题

If 语句貌似只能在sp里面使用。。在nav里面测试只能在sp使用

@变量可以直接使用。。

或者可以使用selectKey 来绑定到 myb变量


Multi-db vendor support
一个配置了"_databaseId"变量的 databaseIdProvider 对于动态代码来说是可用的，这样就可以根据不同的数据库厂商构建特定的语句。比如下面的例子：
<insert id="insert">
  <selectKey keyProperty="id" resultType="int" order="BEFORE">
    <if test="_databaseId == 'oracle'">
      select seq_users.nextval from dual
    </if>
    <if test="_databaseId == 'db2'">
      select nextval for seq_users from sysibm.sysdummy1"
    </if>
  </selectKey>
  insert into users values (#{id}, #{name})</insert>



