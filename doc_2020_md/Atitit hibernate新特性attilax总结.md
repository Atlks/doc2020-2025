Atitit hibernate3 hinernate4 hibernate5新特性attilax总结

1.1. Hibernate3的新特性 	1
1.2. hibernate4.1版本中的新特性和hibernate3.3部分区别 - WTOM的博客 - 博客频道 - CSDN.NET.html	1
1.3. Hibernate 5.1.0 正式版发布，新版本带来了一些新特性及功能增强 201602	2
1.4. 参考资料	2

Hibernate3的新特性 
  相对于Hibernate2，Hibernate3版本的变化包括三个方面： 

      （1）API的变化 
     （2）元数据 

      元数据主要是指Hibernate映射文件中各种元素和属性的用法的变化。首当其冲的是Hibernate映射文件的文档类型定义，即DTD文件发生了变化，这一点程序员可以从任何一个Hibernate3的映射文件的文件头中发现，即在元素中定义的URL从http://hibernate.sourceforge.net/hibernate-mapping-2.0.dtd变成了http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd。 

      还有一个重大的改变就是lazy属性的默认值从false变成了true，这也是Hibernate从优化应用程序性能的角度出发所做出的决定。因为当lazy=false时，Hibernate对所有字段都采取预先抓取的策略，如果程序员希望采用延迟加载，必须手工在映射文件中将lazy属性的值设为true，然而总是采用预先抓取策略势必会造成极大的资源占用，从而降低应用程序的性能。所以从应用程序的角度来讲，更希望lazy的默认值是true，这样在有需要的时候才去采用预先抓取的检索策略。 

     （3）HQL查询语句 

      Hibernate3 采用新的基于ANTLR的HQL/SQL查询翻译器，不过，Hibernate2的查询翻译器也依然存在。在Hibernate的配置文件中，hibernate.query.factory_class属性用来选择查询翻译器。 

hibernate4.1版本中的新特性和hibernate3.3部分区别 - WTOM的博客 - 博客频道 - CSDN.NET.html

Hibernate 5.1.0 正式版发布，新版本带来了一些新特性及功能增强 201602

Entity joins (or ad hoc joins)


load-by-multiple-id API


CDI 集成的改进


@Embeddables and all null column values


Envers audit queries can now refer to to-one associtions


参考资料
Hibernate3和4版本的不同 - iaiti的专栏 - 博客频道 - CSDN.NET.html
Hibernate 3新特性介绍及发展趋势 - Hibernate - ITeye知识库频道.html
Hibernate 5.1.0 正式版发布 - 开源中国社区.html

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

