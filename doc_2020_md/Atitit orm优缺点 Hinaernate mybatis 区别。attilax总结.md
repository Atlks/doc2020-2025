Atitit orm优缺点 Hinaernate mybatis 区别。attilax总结

1.1. ORM最大的优势。        隐藏了数据访问细节，可移植数据库，适合产品模式	1
1.2. 最大缺点：完全的orm，复杂学习成本	1
1.3. Hinaernate mybatis 区别。。	1
1.4. 适用场景  产品模式hibernate  项目模式mybatis	2
1.5. 走势图	2
1.6. 未来趋势判断 oodb与sql进一步标准化	2
1.7. 参考资料	3

ORM最大的优势。        隐藏了数据访问细节，可移植数据库，适合产品模式

使开发更加对象化 3）
可以很方便地引入数据缓存之类的附加功能

最大缺点：完全的orm，复杂学习成本
自动化意味着映射和关联管理，代价是牺牲性能
复杂学习成本 并不能完全的屏蔽掉数据库层的设计
 对于复杂查询，ORM仍然力不从心。虽然可以实现，但是不值的。视图可以解决大部分calculated column，case ，group，having,order by, exists，但是查询条件(a and b and not c and (d or d))
在处理多表联查、where条件复杂之类的查询时，ORM的语法会变得复杂且猥琐

Mybatis这类半自动orm，学习成本要低些
Hinaernate mybatis 区别。。


hibernate的"跨数据库"的特性是其最大的特点，也是最大的优点。 其它的优点或缺点相对于这一个特性来说, 完全不值得一提.
适用场景  产品模式hibernate  项目模式mybatis
产品模式，需要移植数据库，适用hibernate更好。
项目模式，无需更换数据库，适用mybatis，成本低，快速上手

可以混合使用，单表简单操作用hb，复杂查询用mybatis

走势图
找了半天没有找到
Hibernate vs MyBatis _ LibHunt.html


未来趋势判断 oodb与sql进一步标准化
Oodb可能会流行，从而终结orm
20年前，sql作为数据操作dsl，现在依然没有多大变化，看来未来20年很可能也比较稳固。。

随着sql的进一步标准化，hb的移植数据库的意义会大大降低
在oodb时代，数据库依然需要一个dsl，sql依然会是一个必然选择。当然oo api也会提供

参考资料
atitit.orm的缺点与orm框架市场占有率，选型attilax总结 - 数据库其他综合 - 红黑联盟.html
ORM的优缺点 - sgear - 博客频道 - CSDN.NET.html
ORM的优缺点 - 博客频道 - CSDN.NET.html
ORM框架使用优缺点.html


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

