Atitit  sql art 艺术 attilax著 v4 u55.docx
Atitit 数据库系统原理与设计与sql概论 attilax著 4c.docx

1. 索引引擎	3
1.1. 1. 索引的分类1	3
1.2. 1.1. 按照存储结构划分btree,hash,bitmap,fulltext1	3
1.3. 1.2. 索引的类型  按查找方式分，两种，分块索引 vs编号索引1	3
1.4. 1.3. 顺序索引  vs 散列索引2	3
1.5. 1.4. 按索引与数据的查找顺序可分为 正排与倒排索引2	3
1.6. 1.5. 单列索引与多列索引 复合索引2	3
1.7. 1.6. 分区索引和全局索引 2	3
1.8. 1.7.  Trie树一般指字典树 又称单词查找树，Trie树2	3
1.9. 1.8. 稠密索引 vs 稀疏索引3	3
1.10. 1.9. 多级索引 vs 单击索引3	3
1.11. 1.10. 索引模式extent和blockmap3	3
1.12. 2. 索引建立，更新的流程使用触发更新索引的事件4	3
1.13. 3. ISAM算法 索引顺序存取方法”（Indexed Sequential Access Method） 索引常用的存储结构 B树文件 叫做“，缩写为。4	4
1.14. 4. 索引文件的合并问题5	4
1.15. 分布式存储的索引	4
1.16. 排重索引 Unique索引 Union unique	4
2. 约束	4
2.1. 外键约束	4
2.2. unique	4
3. sql与Sql引擎	5
3.1. 常用sql select update delete	5
3.2. 条件where sql  排序	5
3.3. 数据库翻页  limit offset系列	5
3.4. 多表join  子查询	5
3.5. 替换replace into 语句与on unique 模式	5
4. 报表与统计sql	5
4.1. 分组groupby	5
4.2. 聚合统计函数	5
5. 标准库函数	6
5.1. 加密解密与二进制转换函数	6
5.2. 数学系列	6
5.3. 字符串系列	6
5.4. 日期运算系列	6
5.5. 控制流程函数 条件判断函数；	6
5.6. 5 搜索函数	6
5.7. 6 加密函数	6
5.8. 7 信息函数	6
5.9. 8 其他函数	6
5.10. 9 聚合函数	6
5.11. 系统信息函数；	6
5.12. 格式化函数；	6
6. 数据库Sql编程，存储过程sp，视图触发器	7
6.1. Sp存储过程	7
6.2. Udf自定义函数	7
6.3. Trigger触发器	7
6.4. View视图	7
6.5. 游标	7
6.6. 存储过程异常处理	7
7. 元数据系列	7
8. Sql标准化	8
8.1. 1. Sql标准化的历史3	8
8.2. 1.1. Sql92标准4	8
8.3. 1.2. Sql99标准4	8
8.4. 1.3. SQL:2003为例，它包括以下9个部分 5	8
8.5. 1.4. Sql2006标准6	8
8.6. 1.5. Sql2008标准7	8
8.7. 1.6. SQL:2011 7	8
9. Sql性能优化与explain	8
10. Sql解析与美化	8
10.1. 源码高亮	8
10.2. Sql解析	8
11. 数据库新特性	8
12. 常用的数据库算法	9
12.1. Join算法	9
12.2. Groupby算法	9
12.3. 聚合union算法	9
13. 参考书籍	9

  索引引擎
1. 索引的分类1
1.1. 按照存储结构划分btree,hash,bitmap,fulltext1
1.2. 索引的类型  按查找方式分，两种，分块索引 vs编号索引1
1.3. 顺序索引  vs 散列索引2
1.4. 按索引与数据的查找顺序可分为 正排与倒排索引2
1.5. 单列索引与多列索引 复合索引2
1.6. 分区索引和全局索引 2
1.7.  Trie树一般指字典树 又称单词查找树，Trie树2
1.8. 稠密索引 vs 稀疏索引3
1.9. 多级索引 vs 单击索引3
1.10. 索引模式extent和blockmap3
2. 索引建立，更新的流程使用触发更新索引的事件4
3. ISAM算法 索引顺序存取方法”（Indexed Sequential Access Method） 索引常用的存储结构 B树文件 叫做“，缩写为。4
4. 索引文件的合并问题5

分布式存储的索引
排重索引 Unique索引 Union unique 

约束 

外键约束
 unique
Atitit linq 和sql 原理与概论

sql与Sql引擎
常用sql select update delete 
条件where sql  排序
数据库翻页  limit offset系列
多表join  子查询
Merge数据融合 替换replace into 语句与on unique 模式
适合替换模式更加简单。On unique适合主键不变模式比较繁琐
报表与统计sql
分组groupby
聚合统计函数

标准库函数
加密解密与二进制转换函数
数学系列
字符串系列
日期运算系列
控制流程函数 条件判断函数；
 5 搜索函数
6 加密函数
7 信息函数
8 其他函数
9 聚合函数
系统信息函数；
格式化函数；




 数据库Sql编程，存储过程sp，视图触发器
Sp存储过程
Udf自定义函数
Trigger触发器
View视图
游标
存储过程异常处理
 元数据系列

Sql标准化
1. Sql标准化的历史3
1.1. Sql92标准4
1.2. Sql99标准4
1.3. SQL:2003为例，它包括以下9个部分 5
1.4. Sql2006标准6
1.5. Sql2008标准7
1.6. SQL:2011 7
Sql性能优化与explain
 Sql解析与美化
源码高亮
Sql解析

 数据库新特性
atitit.Windows Server 2003 2008 2012系统的新特性 attilax 总结 - attilax的专栏 - 博客频道 - CSDN.NET.html

 常用的数据库算法
Join算法
Groupby算法
聚合union算法
 
 
参考书籍
2. 参考数据库系统导论 (豆瓣).html	2
3. 数据挖掘--概念与技术》、	3
4. 《数据库系统概念(原书第6版)（数据库系统方面的经典教材，被国外许多知名大学采用。	3
5. 5.《数据库原理、编程与性能》	5
6. 、6.《数据库系统实现》、	5
7. 7.《数据库处理--基础、设计与实现》	5
8. Sql原理	5
9. 《自己动手设计数据库》(Michael...)【简介_书评_在线阅读】 - 当当图书.html	5
10. 《分布式数据库系统原理（第3版）（世界著名计算机教材精选）》(（德）厄兹叙...)	6
10.1. 《MySQL技术内幕:InnoDB存储引擎》	8
10.2. 《数据库系统导论》（第七版）C.J.Date著 数据库领域中的权威著作	9
10.3. 《数据库系统概念》（第	9
10.4. MicrosoftSQLServer2008技术内幕	9
Atitit。sql2016标准化的规划方案 v3 q2a-布布分享-bubufx.com.html
Atitit.跨语言数据库db  api兼容性 jdbc odbc ado oledb 增强方案.html
Atitit.数据索引 的种类以及原理实现机制 索引常用的存储结构 - attilax的专栏 - 博客频道 - CSDN.NET.html
Atitit.常用分区api的attilax总结_oracle数据库_ThinkSAAS.html
Atitit.数据库分区的设计 attilax  总结_oracle数据库_ThinkSAAS.html
Atitit.数据库存储引擎的原理与attilax 总结 - attilax的专栏 - 博客频道 - CSDN.NET.html
Atitit.数据库事务隔离级别attilax总结 - 百科教程网_经验分享平台[爱学艺经验教程频道].html


作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher  kok  虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak 万兽之王
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 
埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com


 --Atiend  v8

