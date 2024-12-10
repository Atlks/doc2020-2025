Atitit mybatis翻页pagehelper 物理分页法


①.导入依赖  pagehelper

<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper</artifactId>
    <version>3.4.2</version>
</dependency>
<dependency>
    <groupId>com.github.jsqlparser</groupId>
    <artifactId>jsqlparser</artifactId>
    <version>0.9.1</version>
</dependency>
1
2
3
4
5
6
7
8
9
10
②.在全局配置文件中配置插件

<plugins>
    <!-- com.github.pagehelper为PageHelper类所在包名 -->
    <plugin interceptor="com.github.pagehelper.PageHelper">
        <!-- 方言 -->
        <property name="dialect" value="mysql"/>
        <!-- 该参数默认为false -->
        <!-- 设置为true时，使用RowBounds分页会进行count查询 -->
        <property name="rowBoundsWithCount" value="true"/>
    </plugin>
</plugins>
--------------------- 
版权声明：本文为CSDN博主「咸鱼SAO」的原创文章，遵循CC 4.0 by-sa版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_38977097/article/details/81395876
翻页代码
public class dataExecuter {

    public static void main(String[] args) throws IOException, OgnlException {

        String sql_id = "warning_query";
        SqlSessionFactory sqlSessionFactory = MybatisUtil. getSqlSessionFactory();
        SqlSession session = sqlSessionFactory.openSession(true);
        // api ��Ϊ[ openSession(boolean autoCommit) ]���ò���ֵ���������Ƹ� sqlSession �Ƿ��Զ��ύ��true��ʾ�Զ��ύ��false��ʾ���Զ��ύ[���޲εķ�������һ�£������Զ��ύ]

        //设置分页条件，Parameters:pageNum 页码pageSize 每页显示数量count 是否进行count查询
        PageHelper.startPage(1, 3, true);
       // PageHelper.startPage(1,10);
//此时已经分页了
        List<Map>  rzt_list = session.selectList(sql_id,null);

      //  可以使用PageInfo 查看分页信息
        PageInfo pageInfo = new PageInfo<>(rzt_list);
        System.out.println(JSON.toJSONString(pageInfo));
        System.out.println(JSON.toJSONString(rzt_list, true));

    }


{"endRow":0,"firstPage":0,"hasNextPage":false,"hasPreviousPage":false,"isFirstPage":true,"isLastPage":false,"lastPage":0,"list":[],"navigatePages":8,"navigatepageNums":[],"nextPage":0,"pageNum":1,"pageSize":3,"pages":0,"prePage":0,"size":0,"startRow":0,"total":0}
[]

//打印分页信息
    System.out.println("数据总数：" + pageInfo.getTotal());
    System.out.println("数据总页数：" + pageInfo.getPages());
    System.out.println("最后一页：" + pageInfo.getLastPage());
--------------------- 



{"endRow":3,"firstPage":1,"hasNextPage":true,"hasPreviousPage":false,"isFirstPage":true,"isLastPage":false,"lastPage":2,"list":[
],"navigatePages":8,"navigatepageNums":[1,2],"nextPage":2,"pageNum":1,"pageSize":3,"pages":2,"prePage":0,"size":3,"startRow":1,"total":4}



PageInfo的方法



(9+条消息)MyBatis 框架学习——Mybatis分页之PageHelper插件 - 子非鱼焉 - CSDN博客.html
