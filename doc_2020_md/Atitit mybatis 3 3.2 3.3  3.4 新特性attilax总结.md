Atitit mybatis 3 3.2 3.3  3.4 新特性attilax总结

1. 新特性历史	1
1.1. iBATIS 3 内的新特性.html	1
1.2. MyBatis团队于2013年2月21日正式发布 MyBatis 3.2.0	1
1.3. MyBatis 3.3.0 发布，此版本主要有两个改进：	2
1.4. 持久层框架 MyBatis v3.4.1 发布 2016-06-26 	2
2. Mybatis直接执行sql的改进 SqlMapper	2
2.1. SqlMapper提供的方法	3
3. 参考资料	5

新特性历史
iBATIS 3 内的新特性.html
随着开发团队转投Google Code旗下，ibatis3.x正式更名为Mybatis 
MyBatis团队于2013年2月21日正式发布 MyBatis 3.2.0
新特性包括:
支持可扩展脚本引擎
支持可扩展字节码提供器和Java辅助类
缓存嵌套查询
改善日志
修正了40余处BUG

MyBatis 3.3.0 发布，此版本主要有两个改进：

Ognl 升级至最新版本 3.0.11 


默认代理工具是 Javassist，放置在 mybatis jar 内


持久层框架 MyBatis v3.4.1 发布 2016-06-26 
更新日志
改进
Allow referencing parameters by their declared names when compiled with Java 8 -parametersoption. #549
Added auto-detection of Year/MonthTypeHandler added in mybatis-typehandlers-jsr310 1.0.1. #646
@Select can now return an array of objects. #669
Allow specifying custom reflectorFactory in XML config. #657

Mybatis直接执行sql的改进 SqlMapper
为了让通用Mapper更彻底的支持多表操作以及更灵活的操作，在2.2.0版本增加了一个可以直接执行SQL的新类SqlMapper。
通过这篇博客，我们来了解一下SqlMapper。
SqlMapper提供的方法
SqlMapper提供了以下这些公共方法：

Map<String,Object> selectOne(String sql)


Map<String,Object> selectOne(String sql, Object value)


<T> T selectOne(String sql, Class<T> resultType)


<T> T selectOne(String sql, Object value, Class<T> resultType)


List<Map<String,Object>> selectList(String sql)


List<Map<String,Object>> selectList(String sql, Object value)


<T> List<T> selectList(String sql, Class<T> resultType)


<T> List<T> selectList(String sql, Object value, Class<T> resultType)


int insert(String sql)


int insert(String sql, Object value)


int update(String sql)


int update(String sql, Object value)


int delete(String sql)


int delete(String sql, Object value)

//查询，返回List<Map> List<Map<String, Object>> list = sqlMapper.selectList("select * from country where id < 11")
//insert int result = sqlMapper.insert("insert into country values(1921,'天朝','TC')"); 
//update result = sqlMapper.update("update country set countryname = '天朝' where id = 35"); 
//delete result = sqlMapper.delete("delete from country where id = 35");

参考资料

持久层框架 MyBatis v3.4.1 发布 - OPEN资讯.html
MyBatis 3.3.0 发布，Ognl 升级至版本 3.0.11 - 开源中国社区.html
ibatis2.x与mybatis(ibatis3.x)的比较 - 赵先生不知何许人也的日志 - 网易博客.html
MyBatis直接执行SQL的工具SqlMapper - 偶尔记一下 - 博客频道 - CSDN.NET.html


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

