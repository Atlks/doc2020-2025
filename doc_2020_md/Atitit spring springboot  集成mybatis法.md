Atitit spring springboot  集成mybatis法

使用spring管理数据源。。需要修改spring、 配置

SpringBoot-配置Mybatis-yml方式 - KuroNJQ - 博客园.html

直接代码集成，无需修改任何配置
D:\00wkspc\v2\intelligence\apiserver\src\main\java\org\chwin\firefighting\apiserver\data\MybatisUtil.java
直接读取spring、 yml、配置文件，读取到数据库配置，然后生成factory

步骤，读取yml，文件，使用ongl定位到url pwd usr
读取mybatis模板配置，，替换其中的mysql url等参数。。
注意xml转义符号
使用SqlSe



public class mybatisdemo {
   public static void main(String[] args) throws Exception {

      SqlSessionFactory sqlSessionFactory =MybatisUtil. getSqlSessionFactory();

      SqlSession session = sqlSessionFactory.openSession(true);
   // api ��Ϊ[ openSession(boolean autoCommit) ]���ò���ֵ���������Ƹ� sqlSession �Ƿ��Զ��ύ��true��ʾ�Զ��ύ��false��ʾ���Զ��ύ[���޲εķ�������һ�£������Զ��ύ]

      MybatisMapperCls mapper = session.getMapper(MybatisMapperCls.class);

      // List li =mapper.queryall();



      List<Map> li = mapper.query("select * from tab1");
      System.out.println(JSON.toJSONString(li, true));
      session.close();
      // = session.selectList(arg0);

   }



Ref
 Atitit mybatis spring整合。读取spring、yml、文件的mysql url 步骤，读取yml，文件，使用ongl定位到url pwd usr 读取mybatis模板配置，
