Atitit mybatis快速开发 的sql api接口

1.1. sql模式 开发速度大大快与 映射模式	1
1.2. MyBatis Mapper	1
1.2.1. 代码	2
1.2.2. 原理	2
1.3. 参考资料	3


  sql模式 开发速度大大快与 映射模式
MyBatis Mapper
可能有些人也有过类似需求，一般都会选择使用其他的方式如Spring-JDBC等方式解决。
能否通过MyBatis实现这样的功能呢？
为了让通用Mapper更彻底的支持多表操作以及更灵活的操作，在<b>2.2.0版本</b>增加了一个可以直接执行SQL的新类SqlMapper。
注：3.3.0版本去掉了这个类，这个类现在在EntityMapper项目
EntityMapper是通用Mapper2.x版本中的一部分，通用Mapper3.x以后将EntityMapper移出了通用Mapper，所以EntityMapper独立出来。
建议使用通用Mapper，通用Mapper3更强大，通用方法更多，更方便扩展。

代码
import com.github.abel533.sql.SqlMapper;

原理


  public List<Map<String, Object>> selectList(String sql) {
        String msId = msUtils.select(sql);
        return sqlSession.selectList(msId);
}

Msid SELECT.-1361880592
/palmWin/src/main/java/com/github/abel533/sql/SqlMapper.java


    private String select(String sql) {
            String msId = newMsId(sql, SqlCommandType.SELECT);
            if (hasMappedStatement(msId)) {
                return msId;
            }
            StaticSqlSource sqlSource = new StaticSqlSource(configuration, sql);
            newSelectMappedStatement(msId, sqlSource, Map.class);
            return msId;
        }

StaticSqlSource是mybatis提供的类库

参考资料
MyBatis直接执行SQL的工具SqlMapper - abel533的个人页面.html
MyBatis直接执行SQL的工具SqlMapper - abel533的个人页面.html


作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com
 
 
头衔：uke总部o2o负责人，全球网格化项目创始人，
uke交友协会会长  uke捕猎协会会长 Emir Uke部落首席大酋长，
 
uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长，
 
uke 首席cto   软件部门总监 技术部副总监  研发部门总监主管  产品部副经理 项目部副经理   uke科技研究院院长uke软件培训大师
 
uke波利尼西亚区大区连锁负责人 汤加王国区域负责人 uke克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke布维岛和南乔治亚和南桑威奇群岛大区连锁负责人
 Uke软件标准化协会理事长理事长 Uke 数据库与存储标准化协会副会长
 
uke终身教育学校副校长   Uke医院 与医学院方面的创始人
 uec学院校长， uecip图像处理机器视觉专业系主任   uke文档检索专业系主任
Uke图像处理与机器视觉学院首席院长
Uke 户外运动协会理事长  度假村首席大村长   uke出版社编辑总编
 
转载请注明来源：attilax的专栏  ?http://blog.csdn.net/attilax
--Atiend  v8

