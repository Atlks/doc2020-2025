Atitit enhance dev effect提升开发效率的十大原理与方法v3  u66.docx
Atitit enhance dev effect提升开发效率的十大原理与方法v2 u66.docx
Atitit enhance dev effect提升开发效率的十大原理



管理
去中心化 下放决策
市场通常是组织经济活动的一种好方法
2014年之前大部分曾经是中央计划经济的国家已经放弃了这种制度，并努力发展市场经济。在一个市场经济（marketeconomy）中，中央计划者的决策被千百万企业和家庭的决策所取代。这些企业和家庭在市场上相互交易，价格和个人利益引导着他们的决策。
自己决策最快速的方法，语言工具

综合交互利用lib，避免单打独斗

原理五
贸易能使每个人状况更好
也许你在新闻中听到过，在世界经济中日本人是美国人的竞争对手。实际上，两国之间的贸易可以使两个国家的状况都变得更好。从某种意义上说，经济中每个家庭都与所有其他家庭竞争。尽管有这种竞争，但把你的家庭与所有其他家庭隔绝开来并不会使大家过得更好。通过与其他人交易，人们可以按较低的成本获得各种各样的物品与劳务。

 沟通与反馈	18
15.1. 集中式开发	1815.2. 适当的全栈	18
15.3. 每日会议 daily report	1815.4. Train and  ted	18
Lan lib tool 模式
代码抽象层次 method》sttic 》》dynmaic method
避免过度设计
驳回需求不合理，二期实现
开发理念轻量化
不要追随大公司解决方案 不要过度设计 不要三层 不要bean模式
以数据库为中心，不要域模型模式

不要dto vo bo do等域模式
简化设计，避免重型方法类模式，大力减少类数量，加快编译速度
通过数据库集成 ，不要3gl api 集成
编程范式  声明式编程  元编程
2. 高效率的编程范式	2
2.1. DP(Declarative Programming)描述性范式	2
2.1.1. 俩种实现模式 LP逻辑编程 FP 函数式编程	2
2.2. LOP  面向语言编程（LOP, Language Oriented Programming）	2
2.3. AOP	3
2.4. 泛型式、元编程、切面式和事件驱动式。	3
2.5. 1.2.5. MP(Meta Programming)	6 2. Table-oriented Programming 7	3

开发方法论 tdd bdd xp
函数》sttaic方法 》》oop
接口设计统用化 向上抽象
比如库表查询接口，操作接口
IDE一体化 tools
简化设计，避免重型方法类模式，大力减少类数量，加快编译速度

减少编译与部署	多使用sql，尽可能少使用java，可以适当使用些脚本js 等b
上传zip unzip by ssh client lib
Git pul部署
13.1. All in one	16
13.2. 内嵌web sesrver （比如springboot一类的）	16
13.3. 单元测试junit  main运行	16
13.4. Ide db view	16
5. 提升语言级别到4gl （对开发效率数量级提升）	9
数据库 sql的大力使用 以数据库为中心 免部署免编译
5.1. 语言的代际关系 （4gl）sql  》（3gl）script  java net c#	9
5.2. 使用4gl dsl语言与api	9
5.3. 免编译 多使用脚本语言js一类	10
5.4. 动态化	10
提升可读性  本地化语言 
中文json 表名等
代码组织结构 循序渐进 block 文件 方法 static 》》对象
Dsl  动态 脚本化
嵌入更高级别的dsl sql  script等
类库固化 dsl lib 
通用性 提升类库扩展性
嵌入dsl sql等提示扩展性
http接口类库
Web jdbc sql查询类接口
接口集成模式 互操作
Db集成》》url集成》》代码集成
通用接口查询与操作
抽象化通用化框架化
库表查询 api  执行sql
不一定要统一的返回模式  sp可以返回多行  灵活 

7. 数据传输与存储层面的优化	12
7.1. Scheme free模式 多使用nosql  json 半结构化数据	12
7.2. Mysql5.7以上可多多 使用json数据	12
7.3. 子母表设计可使用json集合模式等	12
7.4. 适当的反范式设计	12
7.5. 可以跨库调用，可以把次模式看成看成一个调用socket非文本模式接口即可（ 通过数据库驱动）	12


利用现有机制
数据库机制
大力使用mysql event等功能
视图 unique merge约束trigger触发器
尽可能使用数据库unique merge约束trigger触发器等现有功能来简化，配置化

Sp trigge  udf 
视图  event
Unique索引 全文索引 外键等约束机制

Other
热部署  crontab kill and restart
简化流程，直接打通ui到mybatis通道化  单层》双层》三层

